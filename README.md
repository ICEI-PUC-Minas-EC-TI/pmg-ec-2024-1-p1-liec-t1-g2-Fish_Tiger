# Fish Tiger 

* Campus Coração Eucarístico
* Engenharia da Computação
* 1° Semestre
* Laboratório de introdução à Engenharia da Computação, Algoritmos e Estruturas de Dados I, Introdução à Computação


## Integrantes

* Heberty Roger
* João Miguel
* Yago Vinícius


## Orientadores

* Marta Dias Moreira Noronha
* Sandro Jerônimo de Almeida
* Naísses Zóia Lima


## Resumo

No Brasil, aproximadamente 1/5 da população realiza viagens de 11 dias ou mais pelo menos uma vez por ano, e além disso, mais de 11 milhões de pessoas são aquarístas (possuem peixes domésticos) neste mesmo país. Sendo assim, vista a necessidade de realizar a manutenção nos aquários domésticos durante os períodos em que seus respectivos donos estão realizando viagens de longa duração, o projeto Fish-Tiger tem como objetivo eliminar essas preocupações e garantir qualidade de vida para os peixes criados em aquários, realizando troca de água quando houver alterações no pH da mesma.


# Código (do arduino ou esp32)

#include <ESP32Servo.h>
#include "BluetoothSerial.h"

#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run make menuconfig to and enable it
#endif

BluetoothSerial SerialBT; // Cria o objeto Bluetooth
Servo servoEnt; // Cria objeto Servo para saída de água
Servo servoSai; // Cria objeto Servo para saída de água

const int servoEntPin = 25;
const int servoSaiPin = 26;
int ValorLeitura = 8;
int phDesejado;
int analise;

void setup() {
  Serial.begin(9600);
  SerialBT.begin("Figh-Tiger"); // Nome do dispositivo Bluetooth
  Serial.println("Conecte-se Via Bluetooth");
  pinMode(12, OUTPUT);
  pinMode(34, INPUT);
}

void tanque(char ent)
{
  switch(ent)
  {
    case '1':
      servoSai.write(90);
      Serial.println("Tanque esvaziando");
      break;
    case '2':
      servoSai.write(0);
      servoEnt.write(0);
      Serial.println("Tanque estável");
      break;
    case '3':
      servoEnt.write(90);
      Serial.println("Tanque enxendo");
      break;
  }
}

void processo(){
  tanque('1'); // Tanque esvaziando
    delay(2000);
  tanque('2'); // Tanque estável
    delay(2000);
  tanque('3'); // Tanque enxendo
    delay(2000);
  tanque('2'); // Tanque estável
    delay(2000);
}

void loop()
{
  if(SerialBT.available() > 0)
    analise = SerialBT.read();
  switch(analise){
    case '1':
      processo();
      break;
    case '0':
      phDesejado = 10;
      break;
    case '2':
      break;
    default:
      phDesejado = analise - 0;
      break;
  }
  if(phDesejado != ValorLeitura)
    processo();
}

void tanque(char ent)
{
  switch(ent)
  {
    case '1': // Tanque enxendo 
      myservo.write(90);
      break;
    case '2': // Tanque estável
      myservo.write(0);
      break;
    case '3': // Tanque esvaziando
      break;
  }
}

void loop() {
  if(Bluetooth.available() > 0)
     funcao = Bluetooth.Read();
  tanque(funcao);
}

# Aplicativo para Smartphone

<li><a href="App/README.md"> Aplicativo </a></li>


# Apresentação

<ol> // Objetivos Gerais do projeto
     // Objetivos Específicos do projeto
<li><a href="Apresentacao/README.md"> Vídeo do Funcionamento</a></li> // sem meme tem que gravar
<li><a href="Apresentacao/README.md"> Fotos do Projeto</a></li> // sem meme tem que tirar foto
</ol>


# Manual de Utilização

<li><a href="Manual/manual de utilização.md"> Manual de Utilização</a></li>


# Documentação

<ol>
<li><a href="Documentacao/01-Introducão.md"> Introdução</a></li>
<li><a href="Documentacao/02-Metodologias Ágeis.md"> Metodologias Ágeis</a></li>
<li><a href="Documentacao/03-Desenvolvimento.md"> Desenvolvimento </a></li>
<li><a href="Documentacao/04-Testes.md"> Testes </a></li>
<li><a href="Documentacao/05-Conclusão.md"> Conclusão </a></li>
<li><a href="Documentacao/06-Referências.md"> Referências </a></li>
</ol>
