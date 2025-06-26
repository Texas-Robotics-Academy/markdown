# Solution - Exercise 6: Switch Statements

## Exercise 6.1:
{{ site.data.alerts.callout_code_div }}
```
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
    int val = 0;
    cout << "Enter a value: ";
    cin >> val;
    switch(val) {
        case 0:
            cout << "Zero" << endl;
            break;  
        case 1:
            cout << "One" << endl;
            break;  
        case 2:
            cout << "Two" << endl;
            break;  
        case 3:
            cout << "Three" << endl;
            break;
        default:
            cout << "Other" << endl;

    }
    return 0;
}
```
{{ site.data.alerts.end }}

## Exercise 6.2:
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

int counter = 0;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  byte threshold = 10;
  byte left = one.readLeftRangeSensor();
  byte right = one.readRightRangeSensor();
  byte obstacle = 0;
  if(left > threshold) {
    if(right > threshold) {
      obstacle = 3;
    } else {
      obstacle = 2;      
    }
  } else if(right > threshold) {
    obstacle = 1;    
  }  
  
  switch(obstacle) {
    case 0:
      one.lcd1("Neither");
      break;
    case 1:
      one.lcd1("Left");
      break;
    case 2:
      one.lcd1("Right");
      break;
    case 3:
      one.lcd1("Both");
      break;
  }
  
  byte button = one.readButton();
  switch(button) {
    case 0:
      one.lcd2("No Button");
      break;
    case 1:
      one.lcd2("Button 1");
      break;
    case 2:
      one.lcd2("Button 2");
      break;
    case 3:
      one.lcd2("Button 3");
      break;
  }
}
```
{{ site.data.alerts.end }}