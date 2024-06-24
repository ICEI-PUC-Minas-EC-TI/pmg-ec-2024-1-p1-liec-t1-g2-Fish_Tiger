#include <Servo.h>
#include "BluetoothSerial.h"

#define SERVO1 3 // Porta Digital 3 PWM
#define SERVO2 5 // Porta Digital 6 PWM

#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to and enable it
#endif

BluetoothSerial SerialBT;
Servo s1; // Variável Servo 1
Servo s2; // Variável Servo 2

int entrada;

void setup ()
{
  s1.attach(SERVO1);
  s2.attach(SERVO2);
  Serial.begin(9600);
  s1.write(0); // Inicia o motor na posição zero
  s2.write(0); // Inicia o motor na posição zero
  SerialBT.begin("Figh-Tiger"); // Bluetooth device name
}

void tanque(char ent)
{
  switch(ent)
  {
    case '1': // Tanque enxendo 
    	s1.write(90);
    	break;
    case '2': // Tanque estável
    	s1.write(0);
    	s2.write(0);
    	break;
    case '3': // Tanque esvaziando
    	s2.write(90);
    	break;
  }
}

void loop()
{
  if(Serial.available() > 0){
    entrada = Serial.read();
  	tanque(entrada);
  }
  if(SerialBT.available() > 0){
    entrada = SerialBT.read();
    tanque(entrada);
  }
}

Mantenha neste diretório todo o código do Arduino ou ESP. Para isso, salve aqui o arquivo .ino.