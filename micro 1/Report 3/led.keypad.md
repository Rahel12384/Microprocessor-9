## نام آزمایش 
کنترل led با وارد کردن پسورد در کی پد

## کد آزمایش

#include <Keypad.h>

const byte ROWS = 4;

const byte COLS = 4;

char keys[ROWS][COLS] = {

{'1', '2', '3', 'A'},

{'4', '5', '6', 'B'},

{'7', '8', '9', 'C'},

{'*', '0', '#', 'D'}

};

byte rowPins[ROWS] = {9, 8, 7, 6};

byte colPins[COLS] = {5, 4, 3, 2};

Keypad keypad = Keypad(makeKeymap(keys), rowPins, colPins, ROWS, COLS);

const String password = "1234";

String input = " ";

const int ledPin = 10;

void setup() {

pinMode(ledPin, OUTPUT);

digitalWrite(ledPin, LOW);

Serial.begin(9600);

}

void loop() {

char key = keypad.getKey();

if (key) {

Serial.print(key);

if (key == '#') {

  if (input == password) {

    Serial.println("Password is ok :) ");

    digitalWrite(ledPin, HIGH);

  } else {

    Serial.println("Password is Wrong :( ");

    digitalWrite(ledPin, LOW);

  }

  input = "";

} else if (key == '*') {

  input = "";

  Serial.println("Input cleared!");

} else {

  input += key;

}

}

}
## توضیحات

* ورودی رمز عبور: با فشردن کلیدهای کیپد، اعداد وارد شده به‌صورت متوالی خوانده می‌شوند و در رشته‌ای ذخیره می‌گردند.

* کلیدهای ویژه:

    کلید #: بررسی می‌کند که آیا رمز عبور وارد شده با رمز تعریف‌شده در برنامه (1234) مطابقت دارد یا خیر.

       اگر رمز صحیح باشد، پیام "Password Correct!" در سریال مانیتور نمایش داده شده و LED روشن می‌شود.

       اگر رمز اشتباه باشد، پیام "Wrong Password!" نمایش داده شده و LED خاموش باقی می‌ماند.

   کلید *: ورودی فعلی را پاک می‌کند و به کاربر اجازه می‌دهد رمز جدید وارد کند.

LED:
در صورت وارد کردن رمز صحیح، LED روشن می‌شود.

    در صورت وارد کردن رمز اشتباه، LED خاموش می‌ماند.

## توضیحات سخت افزاری

کی پد: پایه‌های ردیف کیپد به پین‌های 6 تا 9 آردوینو متصل می‌شوند. پایه‌های ستون کیپد به پین‌های 2 تا 5 آردوینو متصل می‌شوند.

LED:
    پایه مثبت LED به پین 10 آردوینو متصل می‌شود.
    
    پایه منفی LED از طریق یک مقاومت به زمین (GND) متصل می‌شود.

    * نحوه استفاده

    برنامه را روی آردوینو آپلود کنید. آردوینو را به کیپد و LED طبق اتصالات بالا وصل کنید. رمز عبور "1234" را وارد کنید و کلید # را فشار دهید. اگر رمز صحیح باشد، LED روشن می‌شود. برای پاک کردن ورودی فعلی، کلید * را فشار دهید.


## خروجی آزمایش:

![توضیح تصویر](https://github.com/Rahel12384/Microprocessor-9/blob/main/micro%201/Report%203/IMG_20250107_163455_731.jpg)
