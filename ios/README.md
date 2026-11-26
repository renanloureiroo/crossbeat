# ios/: Crossbeat iOS

App iOS (Swift + SwiftUI). Cobre o que o iOS não expõe por BLE.

## Responsabilidades

- Expor o serviço GATT do Crossbeat (`CBPeripheralManager`, background + state restoration)
- Gravar dados de saúde no HealthKit, com deduplicação por `HKMetadataKeySyncIdentifier`/`HKMetadataKeySyncVersion`
- Buscar aparelho, controle da câmera, contatos e filtros de notificação por app

Notificações e música **não** passam por aqui: o relógio as recebe direto do ANCS e do AMS do iOS.

## Status

Ainda sem código. Ver [docs/arquitetura.md](../docs/arquitetura.md).
