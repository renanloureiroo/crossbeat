# ADR 0003: Apps nativos (Kotlin e Swift)

- **Status:** aceita
- **Data:** 2026-11-26

## Contexto

Seria possível usar uma tecnologia cross-platform (React Native, Flutter, Kotlin Multiplatform) para compartilhar código entre os apps.

## Decisão

- **Wear OS e Android:** Kotlin + Jetpack Compose (Compose for Wear OS no relógio).
- **iOS:** Swift + SwiftUI.

## Motivos

- O Wear OS não tem suporte de primeira classe a React Native nem a Flutter.
- No iOS, o núcleo é Core Bluetooth em background (`CBPeripheralManager` com state restoration) e HealthKit. Essas APIs exigem controle fino do ciclo de vida, e uma camada cross-platform atrapalha mais do que ajuda.
- A UI do app iOS é pequena, então quase não há código de interface a compartilhar.
- O protocolo é compartilhado via protobuf, que gera código para Kotlin e Swift.

## Consequências

- Duas linguagens no repositório.
- Kotlin Multiplatform pode ser reavaliado no futuro para compartilhar o framing do protocolo.
