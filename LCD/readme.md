# LCD
## 1-1. LCD 16x2 "Hello, world!" 출력하기

![](./images/lcd01.png)

## 1-2. LCD 16x2 "Hello, world!" 출력하기 Source code

```c
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup()
{
  lcd.begin (16, 2);
  lcd.print ("Hello, world!!!");
}

void loop()
{
}
```
