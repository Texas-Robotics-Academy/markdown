# Solution - Exercise 3: Variables, delay(), setLED()

## Exercise 3.1
{{ site.data.alerts.callout_code_div }}
```
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
    float x, y;
    cout << "Enter x:   ";
    cin >> x;
    cout << "Enter y:   ";
    cin >> y;
    float area = x * y;
    cout << "Area:  " << area << endl;
    return 0;
}
```
{{ site.data.alerts.end }}

## Exercise 3.2
{{ site.data.alerts.callout_code_div }}
```#include <BnrOneAPlus.h>
#include <SPI.h>

BnrOneAPlus one;

#define SSPIN 2

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  one.lcd1("Texas Robotics");
  one.lcd2("Academy");
  delay(1000);
  one.lcd1("Hook 'em");
  one.lcd2("Horns!");
  delay(1000);
}


```
{{ site.data.alerts.end }}

## Exercise 3.3
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
#include <SPI.h>

BnrOneAPlus one;

#define SSPIN 2

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  one.setLed(true);
  delay(1000);
  one.setLed(false);
  delay(1000);
}

```
{{ site.data.alerts.end }}