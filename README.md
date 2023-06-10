# Practica DHT22 con LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y un LCD 16x2 (I2C) para medir temperatura y humedad .

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno y (```LCD 16x2 (I2C)``` ) para mostrar los datos adquiridos; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/) como simulador.
- Tarjeta ```ESP 32```.
- Sensor ```DHT22```.
- ```LCD 16x2 (I2C)```



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Entramos al simulador [WOKWI](https://https://wokwi.com/) y selecionamos la tarjeta ```ESP 32``` como se muestra en la siguiente imagen.

![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/ESP32.png?raw=true)


2. Posteriormente se abrirá la terminal de programación y se coloca la siguente programación:

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
  lcd.setCursor(0,0);
  lcd.print("  Jorge Lopez  ");
  lcd.setCursor(0,1);
  lcd.print(" Sensor de H y T ");
  delay (1000);
}

```
3. Se necesita instalar las librerias de **DHT sensor library for ESPx** y **LiquidCrystal I2C** en el simulador como se muestra en la siguiente imagen.
![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/Libraries.png?raw=true)
 
4. Hacer la conexion de **DHT22** Y **LCD 16x2 (I2C)** con la **ESP32** como se muestra en la siguente imagen.

![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/Conexion%20de%20DHT22%20Y%20LCD%2016x2%20(12C).png?raw=true)

### Instrucciónes de operación

1. Iniciar la simulación.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT22** 

## Resultados

Cuando haya compilado, verás los valores dentro del **LCD 16x2 (I2C)** al igual en el  monitor serial, como muestra en la siguente imagen.

![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/Resultados.png?raw=true)




## Evidencias
![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/Evidencia%201.png?raw=true)

![](https://github.com/jorgelopezquiroz/practica_DHT22_LCD/blob/main/Evidencia%202.png?raw=true)

# Créditos

Desarrollado por Jorge Esteban Lopez Quiroz

- [GitHub](https://github.com/jorgelopezquiroz)