# Código do Arduino/ESP

#include <BluetoothSerial.h>

#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please enable it in menuconfig.
#endif

BluetoothSerial SerialBT;

// Pinos do HC-SR04
#define TRIGGER_PIN 26
#define ECHO_PIN    14

// Pino do LED
#define LED_PIN 12

// Limite para considerar "sensor acionado"
#define DISTANCE_THRESHOLD 10 // cm

// Variável para evitar enviar mensagens repetidas
bool ledState = false; 

void setup() {
  Serial.begin(115200);

  pinMode(TRIGGER_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(LED_PIN, OUTPUT);

  SerialBT.begin("ESP32_SENSOR"); 
  Serial.println("Bluetooth pronto para parear!");
}

long readDistanceCM() {
  digitalWrite(TRIGGER_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIGGER_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIGGER_PIN, LOW);

  long duration = pulseIn(ECHO_PIN, HIGH, 25000);
  if(duration == 0) return 999;

  long distance = duration * 0.034 / 2;
  return distance;
}

void loop() {
  long distance = readDistanceCM();
  Serial.print("Distância: ");
  Serial.println(distance);

  if(distance <= DISTANCE_THRESHOLD) {
    digitalWrite(LED_PIN, HIGH);

    if(!ledState) {  
      ledState = true;
      SerialBT.println("1"); 
      Serial.println("LED ligado → enviando 1");
    }

  } else {
    digitalWrite(LED_PIN, LOW);

    if(ledState) {  
      ledState = false;
      SerialBT.println("0");
      Serial.println("LED desligado → enviando 0");
    }
  }

  delay(200);
}
