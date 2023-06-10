# PRACTICA 2 DHT Y LCD CON MODULO ESP32

## Para esta practica se utilizo 

* Modulo ESP32
* sensor DHT22
* LCD de 3 Pines

Para la simulacion se utilizo la pagina 

woki : https://wokwi.com

## Conexion 

![](https://github.com/AxelMld/Practica2-DHT-y-LCD-ESP32/blob/main/Conexion.png?raw=true)

## Librerias 

1. DHT sensor library for ESPx
2. LiquidCrystal I2C



## Codigo utilizado 


```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
  lcd.setCursor(0, 0);
  lcd.print("  Diplomado AIyM ");
  delay(1000);
  lcd.setCursor(0, 1);
  lcd.print(" Lectura de temp ");
  delay(1000);


}

```


# Resultados
![](https://github.com/AxelMld/Practica2-DHT-y-LCD-ESP32/blob/main/Resultado%201.png?raw=true)


![](https://github.com/AxelMld/Practica2-DHT-y-LCD-ESP32/blob/main/Resultado%202.png?raw=true)

