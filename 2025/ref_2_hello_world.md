# Solution - Exercise 2: Hello World!

## Exercise 2.1
{{ site.data.alerts.callout_code_div }}
```
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
    cout << "Hello world!" << endl;
    return 0;
}
```
{{ site.data.alerts.end }}

# Exercise 2.2
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
  one.lcd1("Hook'em");
  one.lcd2("Horns!");
}

```
{{ site.data.alerts.end }}

# Exercise 2.3
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
  Serial.println("Hello, world!");
}

```
{{ site.data.alerts.end }}