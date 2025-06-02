# LED

## LED 깜빡이기

![](./images/led00.png)

## LED 깜빡이기 Source code

```c
#define LED_BUILTIN 9
void setup()
{
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}
```

## a와 b로 LED 켜고 끄기 Source code
```c
void setup() {
  Serial.begin (9600);
  pinMode (9,OUTPUT);
}

void loop() {
  if(Serial.available() > 0)
{
  char sData = Serial.read();
  if (sData == 'a')
  {
    digitalWrite(9,HIGH);
  }
  else if(sData == 'b')
  {
    digitalWrite(9,LOW);
  }
}
}
```
