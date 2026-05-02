# Mini-project-
The prototype of the Noise Pollution Monitoring System is designed to measure, process, and display environmental noise levels in real time using loT technology. It consists of a sound sensor, a microcontroller (ESP32), and a display unit (LCD), with optional wireless connectivity for data transmission.
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);  // LCD address 0x27
const int soundPin = 34;  // Use ADC pin on ESP32
void setup() {
  Serial.begin(115200);
  lcd.init();
  lcd.backlight();
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Sound Sensor");
  lcd.setCursor(0, 1);
  lcd.print("Initializing...");
  delay(1500);
  lcd.clear();
}
void loop() {
  int rawValue = analogRead(soundPin);   // Reads 0–4095 on ESP32
  // Display on LCD
  lcd.setCursor(0, 0);
  lcd.print("Raw Value:     ");
  lcd.setCursor(0, 1);
  lcd.print(rawValue);
  lcd.print("     ");  // Clear leftover digits

  // Debug in Serial Monitor
  Serial.print("Raw Value: ");
  Serial.println(rawValue);

  delay(200);
}
