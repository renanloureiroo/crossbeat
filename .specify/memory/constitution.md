# Constituição do Crossbeat

## Princípios

### I. Conexão dupla é inegociável
O relógio permanece pareado oficialmente com o Android (Galaxy Wearable, Samsung Health, LTE, firmware). O Crossbeat adiciona a conexão com o iPhone; nunca a substitui. Nenhuma funcionalidade pode exigir desparear o relógio do Android.

### II. Só apps do Crossbeat
No relógio e nos celulares rodam apenas apps do Crossbeat. Merge, LibreWear e WearBridge são referência de estudo: nada de dependência, instalação ou cópia de código sem respeitar a licença.

### III. Privacidade: sem servidor e sem telemetria
Dados de saúde e notificações nunca saem dos dispositivos do usuário. O relógio é o hub entre Android e iPhone. Qualquer proposta que envolva servidor exige uma ADR que justifique a exceção.

### IV. Spec-first
Toda funcionalidade começa por uma spec (`/speckit-specify`), passa por plano (`/speckit-plan`) e tarefas (`/speckit-tasks`) antes da implementação. Decisões de arquitetura viram ADR em `docs/adr/`.

### V. Riscos primeiro
Hipóteses técnicas arriscadas (comportamento de BLE, permissões de plataforma, consumo de bateria) são validadas em protótipos descartáveis, no hardware real, antes de virar código de produto. Comportamento em background e reconexão são requisitos, não extras.

### VI. Protocolo como contrato
`protocol/` é a fonte da verdade entre relógio e iOS. Mudanças são retrocompatíveis (campos novos opcionais, números removidos reservados), atualizam `docs/protocolo.md` e as duas implementações no mesmo PR.

### VII. Nativo onde importa
Kotlin + Compose no Wear OS e no Android; Swift + SwiftUI no iOS. Não se introduz camada cross-platform sem ADR.

## Restrições técnicas

- Alvo principal: Galaxy Watch 8 com Wear OS 6; iPhone com iOS 17 ou superior.
- No iOS, BLE em background deve usar state restoration; no relógio, o link precisa sobreviver a reboot.
- Gravações no HealthKit sempre com `HKMetadataKeySyncIdentifier` e `HKMetadataKeySyncVersion`.
- Permissões são pedidas sob demanda, com explicação ao usuário.

## Fluxo de desenvolvimento

- Documentação em português do Brasil; código, identificadores e mensagens de commit em inglês.
- Specs em `specs/NNN-nome/` (gerenciadas pelo Spec Kit).
- PRs devem citar a spec e, quando houver, a ADR correspondente.
- Testes de comportamento BLE exigem validação em hardware real; simulador não conta.

## Governança

Esta constituição prevalece sobre outras práticas do repositório. Alterações exigem PR com justificativa e atualização da versão abaixo (semver: MAJOR para remoção ou redefinição de princípio, MINOR para princípio novo, PATCH para ajuste de texto).

**Version**: 1.0.0 | **Ratified**: 2026-11-26 | **Last Amended**: 2026-11-26
