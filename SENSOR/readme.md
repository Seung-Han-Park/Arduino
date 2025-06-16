# SENSOR

## 1-1. 초음파 거리 센서 (Ver. 4Pin)

![](./images/sensor01.png)

## 1-2. 초음파 거리 센서 (Ver. 4Pin) Source code

```c
int trig = 2;
int echo = 3;
int RED = 8;
int YELLOW = 9;
int GREEN = 10;

void setup ()
{
  Serial.begin (9600);
  pinMode (trig, OUTPUT);
  pinMode (echo, INPUT);
  pinMode (RED, OUTPUT);
  pinMode (YELLOW, OUTPUT);
  pinMode (GREEN, OUTPUT);
}

void loop ()
{
  digitalWrite (trig, HIGH);
  delayMicroseconds (10);
  digitalWrite (trig, LOW);
  
  unsigned long duration = pulseIn(echo, HIGH);
  float distance = ((float)(340 * duration) / 10000) / 2;
  
  Serial.print (distance);
  Serial.println ("cm");
  delay (100);
  
  if (distance > 80)
  {
    digitalWrite (GREEN, HIGH);
    digitalWrite (YELLOW, LOW);
    digitalWrite (RED, LOW);
  }
  
  if (distance > 30 & distance <= 70)
  {
    digitalWrite (GREEN, LOW);
    digitalWrite (YELLOW, HIGH);
    digitalWrite (RED, LOW);
  }
  
  if (distance > 0 & distance <= 30)
  {
    digitalWrite (GREEN, LOW);
    digitalWrite (YELLOW, LOW);
    digitalWrite (RED, HIGH);
  }
}
  
```

## 2-1. Ultrasonic sensor and 12C LCD

![](./images/sensor02.png)

## 2-2. Ultrasonic sensor and 12C LCD, Source code

```c
#include <Adafruit_LiquidCrystal.h>
#define trigPin 2
#define echoPin 3
long duration;
int distance;
Adafruit_LiquidCrystal lcd_1(0);

void setup() 
{
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
  lcd_1.begin(16, 2);
  lcd_1.print("Sensor Value:");
}

void loop() 
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;
  lcd_1.setCursor(0, 1);  
  lcd_1.print("                "); 
  lcd_1.setCursor(0, 1);
  lcd_1.print(distance);
  lcd_1.print(" cm - Andrea");
  delay(500);
}
```
