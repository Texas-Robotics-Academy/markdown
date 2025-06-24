# Solution - Exercise 4: Loops and Global Variables

## Exercise 4.1:
{{ site.data.alerts.callout_code_div }}
```
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
    for(int i = 0; i < 10; i++) {
        if(i > 5) {
            cout << i << " < 5" << endl;
        } else if (i == 5) {
            cout << i << " == 5" << endl;
        } else {
            cout << i << " > 5" << endl;
        }
    }
    return 0;
}
```
{{ site.data.alerts.end }}

## Exercise 4.2
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
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
  String msg = "Counter: " + String(counter);
  one.lcd1(msg);
  delay(100);
  counter++;
}
```
{{ site.data.alerts.end }}