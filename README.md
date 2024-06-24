# Fish Tiger 

* Campus Coração Eucarístico
* Engenharia da Computação
* 1° Semestre
* Laboratório de introdução à Engenharia da Computação


## Integrantes

* Heberty Roger
* João Miguel
* Yago Vinícius


## Orientador

* Marta Dias Moreira Noronha


## Resumo

Descrever resumidamente, em um ou dois parágrafos, o projeto que está sendo desenvolvido.


# Código (do arduino ou esp32)

#include <ESP32Servo.h>
 
Servo myservo;  // Cria objeto myservo
int servoPin = 25;
char funcao = 2;

void setup() {
  ESP32PWM::allocateTimer(0);
  ESP32PWM::allocateTimer(1);
  ESP32PWM::allocateTimer(2);
  ESP32PWM::allocateTimer(3);
  myservo.setPeriodHertz(50);    // standard 50 hz servo
  myservo.attach(servoPin, 500, 2400); // Relaciona o servo ao pino selecionado
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
