## نام آزمایش
نمایش اعداد واردشده در keypad در سریال مانیتور

## کد آزمایش

#include <key.h>

#include <Keypad.h>

const byte ROWS = 4;

char hexaKeys[ROWS][COLS] = {

{'1', '2', '3', 'A'},

{'4', '5', '6', 'B'},

{'7', '8', '9', 'C'},

{'*', '0', '#', 'D'}

};

byte colPins[ROWS] = {5, 4, 3, 2};

byte rowPins[COLS] = {9, 8, 7, 6};

Keypad customKeypad = Keypad( makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS);

void setup() {

Serial.begin(9600);

}

void loop() {

char customKey = customKeypad.getKey();

if (customKey) {

Serial.println(customKey);

}

}





## خروجی آزمایش:
![alt text](https://github.com/Rahel12384/Microprocessor-9/blob/main/micro%201/Report%201/VID_20250107_163447_981.gif)

