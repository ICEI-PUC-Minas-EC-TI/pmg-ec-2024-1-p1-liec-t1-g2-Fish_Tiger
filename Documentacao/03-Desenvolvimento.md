
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

Após a definição do que seria o projeto em si, partimos para o planejamento e montagem na plataforma de simulação TinkerCAD. Lá houveram as primeiros protótipos de códigos e montagens usando o Microcontrolador e os servos motores. Infelizmente, o TinkerCAD não pode usar a conexão bluetooth para se conectar ao App Inventor, o que limitou os avanços do planejamento através da plataforma.
Tendo aprendido a usar os servos-motores na etapa de planejamento, trouxemos o código para a IDE do Arduino e usamos o ESP32 para realizar os primeiros testes envolvendo bluetooth do Fish Tiger. Inicialmente, tivemos certa dificuldade na integração das bibliotecas, uma vez que a biblioteca que foi usada para controle de servos motores no TinkerCAD não é compatível com o ESP32, e sendo assim, foi necessária uma troca por outra que se encaixasse nessa finalidade. No fim, optamos pela biblioteca <ESP32Servo.h>, que possui as exatas mesmas funções de sua equivalente para arduino.
Tendo todas as bibliotecas necessárias adicionadas, usamos o aplicativo Serial Bluetooth Terminal para testar os códigos de troca de dados via bluetooth do app com o ESP32. Nesta etapa não houveram maiores complicações.
Em seguida desenvolvemos o aplicativo através do MIT App Inventor (maiores detalhes no próximo tópico) para ser capaz de dar ao usuário uma interface que se conectasse ao ESP32, e enviasse um comando simples de alteração de nível de água. Em seguida adicionamos a funcionalidade de seleção de nível de pH.


## Desenvolvimento do Aplicativo

Desenvolvemos um aplicativo para dispositivos móveis através do MIT App Inventor para controlar o Fish Tiger.

### Interface

A tela do aplicativo foi pensada para ser simples e intuitiva para o usuário, que deve ser capaz de conhecer e utilizar todas as funções simplesmente por ler a interface. A mesma também possui visual minimalista e a menor quantidade de texto possível.

### Código

Inicialmente são criadas duas variáveis: Passa, e estado, e ambas tem seu valor inicial ajustado para 0.


## Desenvolvimento do Hardware

Diversos componenetes do projeto já eram de posse de membros do grupo, tendo sido necessário comprar somente os servos motores.

### Montagem

O processo de montagem se apresentou o maior desafio em função da entrada e saída água, impossibilitando a passagem para o próximo tópico.
Foram várias tentativas de adaptção para que consegu~issemos pelo menos um protõtipo funcional.
A arquitetura do projeto, de certa forma, é o maior de desafio do trabalho, para que as funcionalidades do aquário sejam coerentes e funcionais. 
O reservatótio precisa de um suporte acima do aquário e um suporte para o aquário de forma que o segundo motor fique em uma posição favorável para o segundo servo-motor e com espaços laterais que comportem os outros dois medidores, sendo o de umidade e o de PH. 
Um protótipo foi criado com dois servos motores para fazer a entrada de água a partir do celular, através do AppInventor.


### Desenvolvimento do Código

Descreva como foi o desenvolvimento do código do arduino/ESP.

## Comunicação entre App e Hardware

Descreva como foi o processo de comunicação entre App e arduino/ESP.
