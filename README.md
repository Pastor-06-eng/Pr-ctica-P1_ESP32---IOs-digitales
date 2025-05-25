# Pr-ctica-P1_ESP32---IOs-digitales
#include <stdint.h>
#include <stdint.h>

// Definir pines para los LEDs
uint8_t green_led = 2; // Pin del LED verde
uint8_t button = 23;   // Pin del botón

bool led_state = false;

//Variables para temporizadores
uint64_t previous_millis_green = 0;


void setup() {
  // Configurar los pines como salida
  Serial.begin(9600);

  pinMode(green_led, OUTPUT);
  pinMode(button, INPUT_PULLUP); // Inicializamos el pin botón como entrada con pull-up
                               // Pull-up significa que el pin está en reposo en HIGH y se activa con LOW

  digitalWrite(green_led, LOW); // Inicializamos el LED rojo como apagado
}

void loop() {
  if (digitalRead(button) == LOW) { // Si el botón está presionado
    delay(50);                      // Pequeño retardo para evitar rebotes
    led_state = !led_state;         // Intercambiamos el valor de led_state
    digitalWrite(green_led, led_state); // Actualizamos el estado del LED
  }
}
