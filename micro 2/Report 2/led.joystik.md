## نام آزمایش
کنترل شدت نور led با joy stick

## کد آزمایش

const int ledpin =9;

const int X_pin = 0;

void setup() {

pinMode(ledpin, OUTPUT);

Serial.begin(9600);

}

void loop() {

int xValue = analogRead(X_pin);

int brightness = map( xValue,0,1023,0,255);

analogWrite(ledpin,brightness);

delay(100);

}

## خروجی آزمایش:
![alt text](https://github.com/Rahel12384/Microprocessor-9/blob/main/micro%202/Report%202/IMG_20250107_174423_377.gif)
