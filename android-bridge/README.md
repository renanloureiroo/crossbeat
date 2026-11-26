# android-bridge/: Crossbeat Bridge

App Android (Kotlin) que roda no celular pareado oficialmente com o relógio.

## Por que existe

Sono (estágios e score), SpO2, temperatura da pele e treinos do Samsung Health não estão disponíveis para apps de terceiros no relógio. Eles só podem ser lidos no Android, pelo **Samsung Health Data SDK**.

## Responsabilidades

- Ler os dados de forma incremental (marca d'água por tipo)
- Enviar ao relógio pela Wearable Data Layer API

## Status

Ainda sem código. Ver [docs/saude.md](../docs/saude.md).
