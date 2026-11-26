# Visão geral

## O problema

O Galaxy Watch 8 (Wear OS 6) só funciona oficialmente com Android:

- A Samsung só oferece suporte ao iPhone nos Galaxy Watch com Tizen (Watch, Active, Active2, Watch3). Do Watch4 em diante, não há suporte a iOS.
- A configuração inicial exige um Android com o Galaxy Wearable e uma conta Samsung. Não existe configuração sem celular nos modelos Wear OS.
- A ativação do eSIM (LTE) depende do app Wearable no Android. Por isso, o LTE não funciona via iPhone.

Quem usa iPhone no dia a dia e tem um Galaxy Watch fica sem notificações, sem controle de chamadas e sem sincronização de saúde com o Apple Health.

## O objetivo

1. **Paridade com o Merge:** notificações, atender e recusar chamadas, controle de música, contatos, buscar aparelho, controle da câmera, filtro de notificações por app, e saúde e treinos no Apple Health.
2. **Conexão dupla (o diferencial):** o relógio continua pareado com o Android, com Galaxy Wearable, Samsung Health, LTE e atualizações de firmware, e ao mesmo tempo atende o iPhone por BLE.
3. **Open source** (MIT).

## Fora de escopo

- **Responder mensagens de verdade.** O ANCS só oferece ações positiva e negativa por notificação (atender/recusar, dispensar). Não há API pública para responder com texto.
- **Áudio de chamada no relógio** (falar pelo relógio). O perfil HFP provavelmente não está exposto para apps de terceiros no Wear OS. Atender e recusar funcionam; o áudio continua no iPhone. Ainda precisa ser validado no hardware.
- **LTE via iPhone.** A ativação do eSIM depende do Galaxy Wearable no Android.
- **Configurar o relógio sem Android.** É obrigatório ter um Android na ativação.
- **Instalar Merge, LibreWear ou WearBridge.** Eles são apenas referência de estudo.

## Concorrentes e referências

| Projeto | Modelo | O que faz | Observações |
|---|---|---|---|
| Merge | Pago (assinatura, 14 dias grátis) | Notificações, chamadas, música, contatos, Apple Health, buscar aparelho, câmera | Referência de paridade de recursos |
| LibreWear | Open source | Notificações, mídia, contatos, bateria | App iOS ainda "em breve" |
| WearBridge | Open source (MIT) | Notificações via ANCS, overlay de chamada | Bem inicial; testado em Pixel Watch 2 e Galaxy Watch. Referência de código |

## Glossário

| Termo | Significado |
|---|---|
| BLE | Bluetooth Low Energy |
| GATT | Generic Attribute Profile: o modelo de serviços e características do BLE |
| Central / Peripheral | Papéis na camada de enlace: quem inicia a conexão (central) e quem anuncia (peripheral) |
| GATT client / server | Papéis de dados: quem lê/assina (client) e quem expõe os serviços (server). São independentes dos papéis central/peripheral |
| Bond | Pareamento com chaves salvas, o que permite reconexão criptografada |
| ANCS | Apple Notification Center Service: serviço GATT do iOS que expõe as notificações |
| AMS | Apple Media Service: serviço GATT do iOS que expõe o controle de mídia |
| Data Layer | Wearable Data Layer API do Google, usada na comunicação entre o celular Android e o relógio |
| Health Services | API do Wear OS para sensores e dados de saúde no relógio |
