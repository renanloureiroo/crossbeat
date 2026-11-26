# Protocolo do serviço GATT do Crossbeat

> **Status: rascunho.** Será fechado antes da primeira linha do app iOS. Qualquer mudança passa por uma spec em `docs/specs/`.

## Serviços usados

### Nativos do iOS (Apple)

O relógio é **GATT client** desses serviços, que estão sempre presentes no iPhone. Eles só ficam acessíveis num link criptografado (bonded).

**ANCS: Apple Notification Center Service**

| Item | UUID |
|---|---|
| Service | `7905F431-B5CE-4E99-A40F-4B1E122D00D0` |
| Notification Source (notify) | `9FBF120D-6301-42D9-8C58-25E699A21DBD` |
| Control Point (write) | `69D1D8F3-45E1-49A8-9821-9BBDFDAAD9D9` |
| Data Source (notify) | `22EAC6E9-24D6-4BB5-BE44-B36ACE7C7BFB` |

- Notification Source: pacotes de 8 bytes (`EventID`, `EventFlags`, `CategoryID`, `CategoryCount`, `NotificationUID` de 4 bytes).
- Control Point: comandos `GetNotificationAttributes` (0), `GetAppAttributes` (1) e `PerformNotificationAction` (2).
- Ações: `Positive` (0) e `Negative` (1). Não existe resposta com texto.

**AMS: Apple Media Service**

| Item | UUID |
|---|---|
| Service | `89D3502B-0F36-433A-8EF4-C502AD55F8DC` |
| Remote Command (write/notify) | `9B3C81D8-57B1-4A8A-B8DF-0E56F7CA51C2` |
| Entity Update (write/notify) | `2F7CABCE-808D-411F-9A0C-BB92BA96C102` |
| Entity Attribute (read/write) | `C6B2F38C-23AB-46D8-A6AB-A3A870BBD5D7` |

### Serviço do Crossbeat (nosso)

Exposto pelo **app iOS** (`CBPeripheralManager`). O relógio é o cliente.

| Item | UUID (a definir) | Propriedades |
|---|---|---|
| Service | `TBD` | |
| `rx` (relógio → iPhone) | `TBD` | write without response |
| `tx` (iPhone → relógio) | `TBD` | notify |
| `info` | `TBD` | read: versão do protocolo e capacidades |

## Framing

As mensagens podem ser maiores que o MTU negociado. Cada mensagem protobuf é dividida em frames:

```
 0        1        2        3        4        5
+--------+--------+--------+--------+--------+--------...
| ver    | flags  | msg_id (u16 LE) | idx    | total  | payload (chunk)
+--------+--------+--------+--------+--------+--------...
```

| Campo | Tamanho | Descrição |
|---|---|---|
| `ver` | 1 byte | Versão do framing (começa em `1`) |
| `flags` | 1 byte | bit 0: requer ack · bit 1: comprimido |
| `msg_id` | 2 bytes | Identificador da mensagem (rolante) |
| `idx` | 1 byte | Índice do chunk (0-based) |
| `total` | 1 byte | Total de chunks |
| `payload` | MTU − 3 − 6 | Fatia do `Envelope` protobuf serializado |

O receptor remonta as mensagens por `msg_id` e descarta remontagens incompletas após um timeout.

## Mensagens (protobuf)

Ver [`protocol/proto/crossbeat/v1/envelope.proto`](../protocol/proto/crossbeat/v1/envelope.proto).

- `Envelope` com `oneof` para cada tipo de mensagem.
- `Hello`: handshake com versão e capacidades dos dois lados.
- `HealthBatch` / `HealthAck`: amostras de saúde com `sync_id` e `sync_version`.
- `FindDevice`, `CameraCommand`, `NotificationFilter`.

## Versionamento

- O pacote protobuf é versionado no caminho (`crossbeat.v1`).
- Campos novos sempre opcionais; campos removidos têm o número **reservado**.
- O `Hello` negocia a maior versão comum. Se não houver versão compatível, o app avisa para atualizar.
