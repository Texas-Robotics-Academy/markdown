# Solution - Exercise 9: The Line Sensor

{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>

#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

class LineFollowerInterface {
public:
  LineFollowerInterface() {}

  void readLineFollower() {
    for(int i=0; i < 8; i++) {
      _adcVals[i] = one.readAdc(i);
    }
  }

  void computeAsterisks() {
    for(int i=0; i < 16; i++) {
      _asterisks[i] = '-';
    }
    _asterisks[2 * _maxAdc] = '*';
    _asterisks[2 * _maxAdc + 1] = '*';
  }

  void findLine() {
    _maxAdc = 0;
    int maxAdcVal = _adcVals[_maxAdc];
    for(int i = 1; i < 8; i++) {
      if(_adcVals[i] > _adcVals[_maxAdc]) {
        _maxAdc = i;
      }
    }
    _linePotential = ((float)_maxAdc - 3.5) / 3.5;
  }

  void printScreen() {
    String lcd1String = String(_maxAdc) + " " + String(_linePotential);
    one.lcd1(lcd1String);
    one.lcd2(_asterisks);
  }

protected:
  char _asterisks[17];
  int _adcVals[8];
  int _maxAdc;
  float _linePotential;
};

LineFollowerInterface lineFollowerInterface;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  lineFollowerInterface.readLineFollower();
  lineFollowerInterface.findLine();
  lineFollowerInterface.computeAsterisks();
  lineFollowerInterface.printScreen();
}
```
{{ site.data.alerts.end }}