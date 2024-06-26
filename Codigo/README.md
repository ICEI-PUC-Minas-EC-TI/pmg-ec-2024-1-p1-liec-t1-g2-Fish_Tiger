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
