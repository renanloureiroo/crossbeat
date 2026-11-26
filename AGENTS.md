# AGENTS.md

Contexto para agentes de IA (Claude Code, Codex, Cursor etc.) que trabalham neste repositório.

## O projeto

Crossbeat: app para usar o Galaxy Watch 8 (Wear OS 6) com iPhone e Android ao mesmo tempo. Leia primeiro [README.md](README.md) e [docs/arquitetura.md](docs/arquitetura.md).

## Regras

- **Spec-first (Spec Kit):** não implemente funcionalidade sem spec em `specs/NNN-nome/`. Use `/speckit-specify` → `/speckit-plan` → `/speckit-tasks` → `/speckit-implement`. Siga a [constituição](.specify/memory/constitution.md).
- **Decisões de arquitetura** viram uma ADR em `docs/adr/`.
- **Protocolo:** qualquer mudança em `protocol/` atualiza `docs/protocolo.md` e as duas implementações (`wear/` e `ios/`) no mesmo PR.
- **Sem servidor e sem telemetria.** Dados de saúde não saem dos dispositivos do usuário.
- **Sem dependência de Merge, LibreWear ou WearBridge.** Eles são só referência de estudo; não copie código sem respeitar a licença.
- Documentação em português do Brasil. Código, identificadores e mensagens de commit em inglês.

## Stack

| Pasta | Stack |
|---|---|
| `wear/` | Kotlin, Compose for Wear OS, Health Services, Android BLE |
| `ios/` | Swift, SwiftUI, Core Bluetooth, HealthKit |
| `android-bridge/` | Kotlin, Samsung Health Data SDK, Wearable Data Layer |
| `protocol/` | Protobuf (proto3) |
