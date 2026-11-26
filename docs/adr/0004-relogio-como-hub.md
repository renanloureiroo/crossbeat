# ADR 0004: O relógio como hub, sem servidor

- **Status:** aceita
- **Data:** 2026-11-26

## Contexto

Os dados completos de saúde (sono, SpO2, treinos do Samsung Health) só podem ser lidos no Android. Eles precisam chegar ao HealthKit no iPhone. Há dois caminhos:

1. Android → relógio (Data Layer) → iPhone (BLE)
2. Android → servidor (por exemplo, um homelab) → iPhone

## Decisão

O caminho 1: **o relógio funciona como hub**, com uma fila persistente.

## Motivos

- Dados de saúde não saem dos dispositivos do usuário.
- Sem infraestrutura para manter, sem custo e sem conta de usuário.
- O relógio já está conectado aos dois celulares.

## Consequências

- Os dados só fluem quando o relógio tem contato com os dois celulares (não necessariamente ao mesmo tempo, graças à fila).
- O throughput do BLE limita volumes grandes, como treinos longos com amostragem alta. Lotes e compressão ajudam.
- Um relay por servidor continua documentado como alternativa, caso a latência seja um problema.
