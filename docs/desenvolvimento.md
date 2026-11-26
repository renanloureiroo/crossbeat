# Ambiente de desenvolvimento

## Hardware necessário

- Galaxy Watch 8 (ou outro Galaxy Watch com Wear OS), já ativado com um celular Android
- Um celular Android (pareamento oficial e `android-bridge`)
- Um iPhone físico. O simulador do iOS não tem Bluetooth
- Um Mac com Xcode (para o app iOS)

## Relógio (`wear/`)

**Ferramentas:** Android Studio (versão estável mais recente) e JDK 17.

**Habilitar a depuração no relógio:**

1. Em *Configurações → Sobre o relógio → Software*, toque várias vezes em *Versão do software* até liberar as opções do desenvolvedor.
2. Em *Opções do desenvolvedor*, ative *Depuração ADB* e *Depurar por Wi-Fi*.
3. Deixe o relógio e o computador na mesma rede Wi-Fi.

**Parear e conectar por Wi-Fi:**

```bash
# Em "Depurar por Wi-Fi" → "Parear novo dispositivo", o relógio mostra IP:porta e um código
adb pair <ip>:<porta-de-pareamento>
adb connect <ip>:<porta>
adb devices
```

**Logs úteis:**

```bash
adb logcat -s Crossbeat:* BluetoothGatt:* BtGatt.GattService:*
```

## iPhone (`ios/`)

- Xcode (versão estável mais recente), alvo iOS 17 ou superior.
- **Assinatura:** com Apple ID gratuito (*Personal Team*), o app instalado expira em 7 dias. TestFlight e distribuição exigem o Apple Developer Program.
- *Capabilities:* Background Modes (`bluetooth-peripheral`, `bluetooth-central`) e HealthKit.
- Para inspecionar o lado BLE durante testes, use nRF Connect ou LightBlue no iPhone. São só ferramentas de desenvolvimento.

## Android (`android-bridge/`)

- Android Studio e JDK 17.
- Samsung Health Data SDK: para ler dados durante o desenvolvimento, ative o **Developer Mode for Data Read** no Samsung Health. Para distribuir o app, é necessária aprovação da Samsung.

## Protocolo (`protocol/`)

- `protoc` ou o plugin de protobuf do Gradle para Kotlin.
- `swift-protobuf` para Swift.
- O código gerado não é versionado (`protocol/gen/`).

## Fluxo de trabalho

O desenvolvimento é **spec-first**: toda funcionalidade começa por uma spec em [`docs/specs/`](specs/). Decisões de arquitetura viram uma [ADR](adr/).
