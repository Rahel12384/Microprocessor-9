## نام ازمایش
راه اندازی joy stick


## کد آزمایش

const int SW_pin = 8;

const int X_pin = 0;

const int Y_pin = 1;

void setup() {

pinMode(SW_pin, INPUT);

digitalWrite(SW_pin, HIGH);

Serial.begin(9600);

}

void loop() {

Serial.print("Switch: ");

Serial.print(digitalRead(SW_pin));

Serial.print(" | ");

Serial.print("X-axis: ");

Serial.print(analogRead(X_pin));

Serial.print(" | ");

Serial.print("Y-axis: ");

Serial.print(analogRead(Y_pin));

Serial.println(" | ");

delay(400);

}
## توضیحات کد

* متغیرها:

SW_pin: پین دیجیتال متصل به خروجی کلید جوی‌استیک.

X_pin: پین آنالوگ متصل به محور X جوی‌استیک.

Y_pin: پین آنالوگ متصل به محور Y جوی‌استیک.

* توابع اصلی:

setup():
   
    تنظیم پین دیجیتال به عنوان ورودی.
    
    فعال‌سازی مقاومت پول‌آپ داخلی برای پین سوئیچ.
    
    مقداردهی اولیه ارتباط سریال.

loop():
    
    خواندن وضعیت کلید جوی‌استیک با استفاده از digitalRead.
    
    خواندن مقدار محورهای X و Y با استفاده از analogRead.
    
    ارسال مقادیر خوانده شده به مانیتور سریال.

## توضیحات سخت افزاری

خروجی سوئیچ جوی‌استیک به پین دیجیتال 8 آردوینو متصل شود.

خروجی محور X جوی‌استیک به پین آنالوگ A0 آردوینو متصل شود.

خروجی محور Y جوی‌استیک به پین آنالوگ A1 آردوینو متصل شود.
GND جوی‌استیک به GND آردوینو متصل شود.

VCC جوی‌استیک به پین 5V آردوینو متصل شود.



## خروجی آزمایش:
![alt text](https://github.com/Rahel12384/Microprocessor-9/blob/main/micro%202/Report%201/animation.gif)

