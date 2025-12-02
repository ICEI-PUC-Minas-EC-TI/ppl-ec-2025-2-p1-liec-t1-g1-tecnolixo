
## Instruções de utilização

## Materiais e Hardware

**Componentes sugeridos:**

| Item                     | Quantidade | Observações                            |
| ------------------------ | ---------- | -------------------------------------- |
| Microcontrolador ESP32   | 1          | Pode usar Arduino Uno também           |
| Sensor de proximidade    | 1-2        | Para detectar quando o lixo é inserido |
| LED indicador (opcional) | 1          | Para sinalizar descarte registrado     |
| Resistor 220Ω            | 1          | Para LED                               |
| Fonte de alimentação     | 1          | 5V USB ou bateria                      |
| Cabos jumper             | Vários     | Para conexão entre componentes         |
| Caixa/lixeira            | 1          | Onde o lixo será depositado            |


## Conexões e Montagem

1. Conecte o **sensor de proximidade** aos pinos do ESP32 conforme indicado no código (`Codigo/Arduino.ino`).
2. Conecte o **LED indicador** a um pino digital, com resistor de 220Ω em série.
3. Forneça alimentação adequada ao microcontrolador e sensores.
4. Coloque os sensores de modo que detectem objetos sendo descartados na lixeira.

> **Dica:** se possível, faça um diagrama de pinos (`pinout`) para referência futura.


## Configuração do Software

### Código do Microcontrolador

1. Abra a pasta `Codigo` no **Arduino IDE** ou **PlatformIO**.
2. Selecione o modelo de placa correto (ESP32 ou Arduino).
3. Verifique e ajuste os pinos conforme seu hardware.
4. Faça upload do código para o microcontrolador.

### Aplicativo

1. Abra a pasta `App` e siga as instruções para instalar dependências (Node.js, React Native, etc, se aplicável).
2. Configure o endereço do ESP32 no app (IP ou Bluetooth, dependendo da implementação).
3. Compile e execute o aplicativo no celular ou emulador.
4. Cadastre um usuário no app para começar a registrar pontos.


## Como usar

1. Coloque a lixeira em um local acessível.
2. Quando um objeto for descartado, o sensor detecta automaticamente e envia o evento para o app.
3. No app, o usuário pode acompanhar seus pontos e histórico de descartes.
4. Incentive o uso repetido para engajar em práticas sustentáveis.


## Testes e Verificação

* Teste o sensor colocando diferentes objetos na lixeira e veja se o LED indica o registro.
* Confirme se o app recebe os pontos corretamente.
* Ajuste a posição do sensor caso algum objeto não seja detectado.


## Observações Importantes

* Proteja o microcontrolador e sensores de chuva ou umidade.
* Evite obstruções que impeçam o sensor de detectar corretamente.
* Para múltiplos usuários, certifique-se de que o app gerencie logins corretamente.


## Estrutura do Repositório

```
TecnoLixo/
├─ Codigo/       -> Código do microcontrolador (Arduino/ESP32)
├─ App/          -> Código do aplicativo
├─ Documentacao/ -> Manuais e diagramas
├─ Fotos/        -> Imagens do projeto
├─ Manual.md     -> Este arquivo
```


## Futuras Atualizações

* Instruções detalhadas de pinagem e montagem.
* Tutorial em vídeo mostrando todo o funcionamento.
* Ranking de usuários no app.
* Melhorias no sensor e detecção de diferentes tipos de lixo.
