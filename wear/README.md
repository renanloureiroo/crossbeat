# wear/: Crossbeat Wear

App Wear OS (Kotlin + Compose for Wear OS). É o coração do Crossbeat.

## Responsabilidades

- Link BLE com o iPhone: bond, reconexão e sobrevivência a reboot
- Cliente ANCS (notificações e chamadas) e AMS (música)
- Overlay de chamada, notificações e tela/tile de mídia
- Health Services e recebimento de dados do `android-bridge` via Data Layer
- Fila persistente de saúde e envio ao app iOS pelo serviço GATT do Crossbeat

## Status

Ainda sem código. Ver [docs/arquitetura.md](../docs/arquitetura.md).

## Rodar

Ver [docs/desenvolvimento.md](../docs/desenvolvimento.md#relógio-wear).
