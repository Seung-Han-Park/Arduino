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
