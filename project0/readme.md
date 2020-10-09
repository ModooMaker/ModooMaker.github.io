모두의 만든 이 청소년어울림마당 참고 자료
=========================================

> 분당정자청소년수련관 청소년어울림마당 체험 관련 참고 자료입니다. 회로도와 아두이노 코드가 담겨있습니다.

회로도
------

![Alt text](https://github.com/ModooMaker/ModooMaker.github.io/blob/master/_posts/arduino/final.ps.png?raw=true)

Arduino 개발 환경 구축
----------------------

Arduino IDE와 LiquidCrystal_I2C 라이브러리를 설치해야 합니다.

Arduino IDE Downlod : [Arduino.cc](https://www.arduino.cc/en/Main/Software)

LiquidCrystal_I2C Downloda : [GitLab](https://gitlab.com/tandembyte/LCD_I2C)

Arduino Code
------------

Arduino Code : [Arduino.cc](https://create.arduino.cc/editor/directorjjun/6393a22a-f716-4111-a3ac-398ddce91207/preview)

#### TEST Code

```c
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27,16,2);  // set the LCD address to 0x27 for a 16 chars and 2 line display

int potPin = 0; //LM35센서로부터 입력을 받을 포트를 아날로그 A0핀으로 설정
float temperature = 0; //온도를 저장할 변수 선언
long val=0; //val 변수 선언

int L = 5;
int R = 4;
int O = 7;
int X = 6;

void setup()
{
  pinMode(L, INPUT_PULLUP);
  pinMode(R, INPUT_PULLUP);
  pinMode(O, INPUT_PULLUP);
  pinMode(X, INPUT_PULLUP);
  lcd.init();                      // initialize the lcd
  lcd.backlight();
  lcd.setCursor(0,0);
}


void loop()
{
  val = analogRead(potPin); //LM35센서로부터 불러온 값을 val변수에 저장
  temperature = (val*4.8828125); //val값을 실제온도*10으로 변환

  lcd.clear();
  lcd.setCursor(0, 0) ; //LCD에 표시할 위치를 2번째 줄 맨앞으로 이동
  lcd.print((long)temperature / 10); //온도의 정수값표시
  lcd.print(".");    //소수점표시
  lcd.print((long)temperature % 10); //소수점이하 온도 표시
  lcd.print((char)223); //ㅇ표시
  lcd.print("C"); //C표시

  if(digitalRead(L) == 0 && digitalRead(R) == 1 && digitalRead(O) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L Button OK");
    delay(100);
  }

  else if(digitalRead(R) == 0 && digitalRead(L) == 1 && digitalRead(O) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("R Button OK");
    delay(100);
  }

  else if(digitalRead(O) == 0 && digitalRead(L) == 1 && digitalRead(R) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("O Button OK");
    delay(100);
  }

  else if(digitalRead(X) == 0 && digitalRead(L) == 1 && digitalRead(R) == 1 && digitalRead(O) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("X Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(R) == 0 && digitalRead(O) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&R Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(O) == 0 && digitalRead(R) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&O Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(X) == 0 && digitalRead(R) == 1 && digitalRead(O) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&X Button OK");
    delay(100);
  }

  else if(digitalRead(R) == 0 && digitalRead(O) == 0 && digitalRead(L) == 1 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("R&O Button OK");
    delay(100);
  }

  else if(digitalRead(R) == 0 && digitalRead(X) == 0 && digitalRead(L) == 1 && digitalRead(O) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("R&X Button OK");
    delay(100);
  }

  else if(digitalRead(O) == 0 && digitalRead(X) == 0 && digitalRead(L) == 1 && digitalRead(R) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("O&X Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(R) == 0 && digitalRead(O) == 0 && digitalRead(X) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&R&O Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(R) == 0 && digitalRead(X) == 0 && digitalRead(O) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&R&X Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(O) == 0 && digitalRead(X) == 0 && digitalRead(R) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("L&O&X Button OK");
    delay(100);
  }

  else if(digitalRead(R) == 0 && digitalRead(O) == 0 && digitalRead(X) == 0 && digitalRead(L) == 1)
  {
    lcd.setCursor(0, 1);
    lcd.print("R&O&X Button OK");
    delay(100);
  }

  else if(digitalRead(L) == 0 && digitalRead(R) == 0 && digitalRead(O) == 0 && digitalRead(X) == 0)
  {
    lcd.setCursor(0, 1);
    lcd.print("ALL Button OK");
    delay(100);
  }

  else
  {
    delay(100);
  }
}
```

#### Project0 by ModooMaker Code

```c
#include <Keyboard.h>
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27,16,2);

int potPin = 0;
float temperature = 0;
long val=0;

const int L = 7;
const int R = 6;
const int U = 5;
const int D = 4;

void setup()
{
  pinMode(L, INPUT_PULLUP);
  pinMode(R, INPUT_PULLUP);
  pinMode(U, INPUT_PULLUP);
  pinMode(D, INPUT_PULLUP);
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);

  Keyboard.begin();
}

void loop()
{
  val = analogRead(potPin); //LM35센서로부터 불러온 값을 val변수에 저장
  temperature = (val*4.8828125); //val값을 실제온도*10으로 변환

  lcd.clear();
  lcd.setCursor(0, 0) ; //LCD에 표시할 위치를 2번째 줄 맨앞으로 이동
  lcd.print((long)temperature / 10); //온도의 정수값표시
  lcd.print(".");    //소수점표시
  lcd.print((long)temperature % 10); //소수점이하 온도 표시
  lcd.print((char)223); //ㅇ표시
  lcd.print("C"); //C표시

  if(digitalRead(L) == 0)
  {
    lcd.setCursor(0, 1);
    lcd.print("L Button");
    Keyboard.press(KEY_LEFT_ARROW);
    delay(100);
    Keyboard.releaseAll();
    delay(100);
  }

  if(digitalRead(R) == 0)
  {
    lcd.setCursor(0, 1);
    lcd.print("R Button");
    Keyboard.press(KEY_RIGHT_ARROW);
    delay(100);
    Keyboard.releaseAll();
    delay(100);
  }

  if(digitalRead(U) == 0)
  {
    lcd.setCursor(0, 1);
    lcd.print("U Button");
    Keyboard.press(KEY_UP_ARROW);
    delay(100);
    Keyboard.releaseAll();
    delay(100);
  }

  if(digitalRead(D) == 0)
  {
    lcd.setCursor(0, 1);
    lcd.print("D Button");
    Keyboard.press(KEY_DOWN_ARROW);
    delay(100);
    Keyboard.releaseAll();
    delay(100);
  }

  else
  {
    delay(100);
  }
}
```

Tetris
------

Tetris : [Tetris](https://modoomaker.github.io/tetris)
