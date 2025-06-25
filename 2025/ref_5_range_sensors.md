# Solution - Exercise 5: Range Sensors

## Exercise 5.1:
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
  byte left = one.readLeftRangeSensor();
  byte right = one.readRightRangeSensor();
  one.lcd1(left);
  one.lcd2(right);
}
```
{{ site.data.alerts.end }}