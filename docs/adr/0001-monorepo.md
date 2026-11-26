# ADR 0001: Monorepo

- **Status:** aceita
- **Data:** 2026-11-26

## Contexto

O Crossbeat tem três apps (Wear OS, iOS e Android) e um protocolo compartilhado entre o relógio e o iOS. O protocolo muda junto com os dois lados.

## Decisão

Um único repositório com `wear/`, `ios/`, `android-bridge/`, `protocol/` e `docs/`.

## Consequências

- Uma mudança de protocolo, junto com as implementações dos dois lados, cabe num único PR.
- A documentação e as specs ficam junto do código.
- Cada app mantém o próprio build (Gradle e Xcode). Não há uma ferramenta de build unificada, e o CI deve filtrar os jobs por caminho.
