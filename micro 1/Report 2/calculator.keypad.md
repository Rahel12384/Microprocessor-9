## نام آزمایش
ماشین حساب با keypad

## کد آزمایش

#include <Key.h>

#include <Keypad.h>

const byte ROWS = 4;

const byte COLS = 4;

float firstNumber = 0;

float secondNumber = 0;

float result = 0;

bool section = false;

int type = 0;

char hexaKeys[ROWS][COLS] = {

{'1', '2', '3', 'A'},

{'4', '5', '6', 'B'},

{'7', '8', '9', 'C'},

{'*', '0', '#', 'D'}

};

byte colPins[ROWS] = {5, 4, 3, 2};

byte rowPins[COLS] = {9, 8, 7, 6};

Keypad customKeypad = Keypad(makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS);

void setup() {

Serial.begin(9600);

}

void loop() {

int button = int(customKeypad.getKey()) - 48;

if (0 <= button && button <= 10) {

Serial.print(button);


if (section == false) {

  firstNumber = firstNumber * 10 + button;

} 

else {

  secondNumber = secondNumber * 10 + button;

}

}

else {

switch (button) {

  case 17://A

    section = true;

    type = 1;

    Serial.print('+');

    break;

  case 18://///B

    section = true;

    type = 2;

    Serial.print('-');

    break;

  case 19:////C

    section = true;

    type = 3;
    
    Serial.print('*');
    
    break;
 
  case 20:////D

    section = true;
 
    type = 4;
 
    Serial.print('/');
 
    break;
 
  case -6:////*

    section = false;
    
    type = 0;
    
    Serial.println(' ');
    
    break;
    
  case -13://///#
    
    Serial.print(" = ");
    
    switch (type) {
    
      case 1:
    
        result = (firstNumber + secondNumber);
    
        break;
    
      case 2:
    
        result = (firstNumber - secondNumber);
    
        break;
    
      case 3:
    
        result = (firstNumber * secondNumber);
    
        break;
    
      case 4:
    
        result = (firstNumber / secondNumber);
    
        break;
    
    }
    
    type = 0;
    
    Serial.println(result);
    
    firstNumber = 0;
    
    secondNumber = 0;
    
    section = false;
    
    break;

}

}

}
## توضیحات کد

   * متغیرها و توابع اصلی:

    firstNumber و secondNumber: دو عدد ورودی که عملیات روی آن‌ها انجام می‌شود.
    
    result: نتیجه عملیات ریاضی.
    
    section: مشخص می‌کند که کاربر در حال وارد کردن عدد اول است یا عدد دوم. 
    
    type: نوع عملیات ریاضی را تعیین می‌کند (1 برای جمع، 2 برای تفریق و غیره).

   * نحوه اجرا:

    با فشار دادن اعداد روی صفحه کلید، اعداد وارد شده در متغیرهای firstNumber و secondNumber ذخیره می‌شوند.
   
    با فشار دادن کلیدهای A, B, C یا D، نوع عملیات انتخاب می‌شود: A: جمع (+) B: تفریق (-) C: ضرب (*) D: تقسیم (/) 
    
    با فشار دادن کلید #، عملیات انجام شده و نتیجه در سریال مانیتور نمایش داده می‌شود. 
    
    با فشار دادن کلید *، تمامی مقادیر ریست می‌شوند.

## توضیحات سخت افزاری

پایه‌های صفحه کلید را به پین‌های آردوینو مطابق جدول زیر متصل کنید:
   
    پین‌های ستون (Columns): 5, 4, 3, 2.
    
    پین‌های ردیف (Rows): 9, 8, 7, 6.

آردوینو را از طریق کابل USB به کامپیوتر متصل کنید.


## خروجی آزمایش:
![alt text](https://github.com/Rahel12384/Microprocessor-9/blob/main/micro%201/Report%202/VID_20250107_163452_111.gif)

