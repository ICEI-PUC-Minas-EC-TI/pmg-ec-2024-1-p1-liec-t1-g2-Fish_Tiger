# Materiais

Os materiais utilizados no projeto foram:
- 1 ESP32;
- 1 Protoboard;
- Vários cabos jumpers;
- 2 Servos motores;
- 1 Sensor de umidade;
- 1 Sensor de PH;
- 2 Compartimentos de água;
- Notebook;
- Dispersor de ração;
  
# Desenvolvimento

Após a definição do que seria o projeto em si, partimos para o planejamento e montagem na plataforma de simulação TinkerCAD. Em seguida desenvolvemos o aplicativo para a conexão via bluetooth pelo celular, e por fim a montagem do protótipo real.

## Desenvolvimento do Aplicativo

Desenvolvemos um aplicativo para dispositivos móveis através do MIT App Inventor para controlar o Fish Tiger.

### Interface

A tela do aplicativo foi pensada para ser simples e intuitiva para o usuário, que deve ser capaz de conhecer e utilizar todas as funções simplesmente por ler a interface. A mesma também possui visual minimalista e a menor quantidade de texto possível.

### Código

- São criadas duas variáveis: Passa, e estado. Ambas tem seu valor inicial ajustado para 0.
- É iniciada uma legenda "EstadoDoBluetooth" em que está escrito "Desconectado".
- São exibidos dois botões: DesconnectButton e Alterar_pH.
- É mostrada uma lista suspensa vazia.
- É exibida na tela uma imagem clicável de um peixe.
- É chamada uma notificação que aparece na tela do usuário dizendo "Toque no peixe para iniciar o processo de troca manualmente", sinalizando a função do único botão que não possui descrição escrita.
- Quando pressionada, a lista suspensa recebe informações das conexões bluetooth realizadas anteriormente no dispositivo. Após selecionar um item na lista suspensa, é feita a tentativa de conexão com ele. Se a conexão obtiver sucesso, a legenda "EstadoDoBluetooth" é alterada para Conectado.
- Se o botão "DesconnectButton" for pressionado, o bluetooth é desconectado e a legenda "EstadoDoBluetooth" é alterada para "Desconectado".
- Se a imagem no centro da tela for pressionada, envia os sinais de texto 1 e 2 para o dispositivo bluetooth conectado.
- Se o botão "Alterar_pH" for pressionado, acontece a verificação da variável "estado". Caso ela seja 0, um deslizador e uma legenda "ValorDoPH" na parte inferior da tela se tornam visíveis, e a variável "estado" tem seu valor alterado para 1. Caso ela já fosse 1, o deslizador e a lengenda "ValorDoPH" deixam de ser visíveis, a variável "Passa" recebe o valor do deslizador arredondado para baixo, e se esse valor for igual a dez, envia via bluetooth a mensagem de texto "0", seguido de "2". Caso contrário, envia o valor da variável Passa seguido da mensagem de texto "2".
- Se, durante o tempo em que estiver visível, a pocisão do deslizador for alterada, a legenda "ValorDoPH" é alterada para o valor do deslizador.

## Desenvolvimento do Hardware

Diversos componenetes do projeto já eram de posse de membros do grupo, tendo sido necessário comprar somente os servos motores.

### Montagem

O processo de montagem se apresentou o maior desafio em função da entrada e saída água, impossibilitando a passagem para o próximo tópico. Foram várias tentativas de adaptção para que consegu~issemos pelo menos um protõtipo funcional. A arquitetura do projeto, de certa forma, é o maior de desafio do trabalho, para que as funcionalidades do aquário sejam coerentes e funcionais. O reservatótio precisa de um suporte acima do aquário e um suporte para o aquário de forma que o segundo motor fique em uma posição favorável para o segundo servo-motor e com espaços laterais que comportem os outros dois medidores, sendo o de umidade e o de PH. Um protótipo foi criado com dois servos motores para fazer a entrada de água a partir do celular, através do AppInventor.

### Desenvolvimento do Código

Nos primeiros testes de desevolvimento do código no TinkerCAD aplicou-se apenas os servos motores, tendo não exigido biblitoecas específicas uma vez que a <Servo.h> é nativa desde simulador (nos processos seguintes, essa biblioteca foi substituída por <ESP32Servo.h>, por ser compatível com o ESP32). Em seguida, já na IDE do Arduino, foi desenvolvida a conexão via bluetooth pelos módulos internos nativos do ESP32 usando a biblioteca "BluetoothSerial.h" para receber as mensagens enviadas pelo aplicativo. Isso foi unido ao código de troca de água construído no TinkerCAD, e a lógica de programação usada para juntar ambas as duas funções foi do tipo Switch Case.

## Comunicação entre App e Hardware

O processo de comunicação entre o aplicativo e o Hardware foi bem simples, visto que o microcontrolador utilizado foi o ESP32, que não precisa de módulos externos para realizar esse tipo de conexão. Usando como base os códigos presentes na documentação da biblioteca, poucas alterações foram necessárias para iniciar a troca de dados entre App e Dispositivo.
