# ADR 0002: Conexão dupla via BLE, sem tirar o relógio do Android

- **Status:** proposta (depende de validação no hardware)
- **Data:** 2026-11-26

## Contexto

As alternativas existentes fazem o relógio funcionar com o iPhone, mas o usuário perde (ou nunca teve) o ecossistema Samsung: Galaxy Wearable, Samsung Health, LTE e firmware. O Watch 8 precisa de um Android pelo menos na ativação.

## Decisão

O relógio fica pareado normalmente com o Android. O app Crossbeat Wear abre uma **conexão BLE adicional** com o iPhone e atua como GATT client do ANCS e do AMS, e como cliente do serviço GATT do Crossbeat.

## Consequências

- O usuário mantém todo o ecossistema Samsung.
- Depende de o rádio e a pilha Bluetooth do relógio sustentarem as duas conexões com estabilidade e consumo de bateria aceitáveis. **Isso precisa ser provado antes de qualquer outra coisa.**
- Se não for viável, a alternativa é o relógio usar só o iPhone depois da ativação, o que elimina o diferencial do projeto.
