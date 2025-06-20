# Solution - Exercise 10: PID Control

{{ site.data.alerts.callout_code_div }}
```#include <BnrOneAPlus.h>
#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

class LineFollowerInterface {
public:
  LineFollowerInterface() {
    for(int i = 0; i < 16; i++) {
      _asterisks[i] = '--';
    }
    _asterisks[16] = 0;
  }

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

  float getLinePotential() {
    return _linePotential;
  }

private:
  char _asterisks[17];
  int _adcVals[8];
  int _maxAdc;
  float _linePotential;
};

LineFollowerInterface lineFollowerInterface;

class PIDController {
protected:
  int _whichItem = 0, _lastButton = 0;
  float _kc = 0.0, _kp = 0.0, _ki = 0.0, _kd = 0.0;
  float _lastError = 0.0, _i = 0.0, _delta = 0.1;
  
public:
  PIDController() {
    
  }
  
  void buttonPress(byte button) {
    switch(button) {
      case 0:
        break;
      case 1:
        if(_lastButton != button) {
          _whichItem++;
          if(_whichItem > 3) {
            _whichItem = 0;
          }
        }
        break;
      case 2:
        switch(_whichItem) {
          case 0:
            _kc += _delta;
            break;
          case 1:
            _kp += _delta;
            break;
          case 2:
            _ki += _delta;
            break;
          case 3:
            _kd += _delta;
            break;
        }
        break;
      case 3:
        switch(_whichItem) {
          case 0:
            _kc -= _delta;
            break;
          case 1:
            _kp -= _delta;
            break;
          case 2:
            _ki -= _delta;
            break;
          case 3:
            _kd -= _delta;
            break;
        }
        break;
    }
    _lastButton = button;
  }
  
  void printScreen() {
    String kcS = _whichItem == 0 ? "*C:" + String(_kc) + " " : "C:" + String(_kc) + " ";
    String kpS = _whichItem == 1 ? "*P:" + String(_kp) + " " : "P:" + String(_kp) + " ";
    String kiS = _whichItem == 2 ? "*I:" + String(_ki) + " " : "I:" + String(_ki) + " ";
    String kdS = _whichItem == 3 ? "*D:" + String(_kd) + " " : "D:" + String(_kd) + " ";
    one.lcd1(kcS + kpS);
    one.lcd2(kiS + kdS);
  }

  void runMotors(float error) {
    float d = error - _lastError;
    _i += error;

    float errorAdjustment = _kp * error + _ki * _i + _kd * d;
    float leftSpeed = _kc + errorAdjustment;
    float rightSpeed = _kc - errorAdjustment;


    if(leftSpeed > 100) leftSpeed = 100;
    if(leftSpeed < -100) leftSpeed = -100;
    if(rightSpeed > 100) rightSpeed = 100;
    if(rightSpeed < -100) rightSpeed = -100;
    
    one.move(leftSpeed, rightSpeed);

    _lastError = error;
  }
};

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

PIDController pid;

/*
 * The values in this implementation did 12.34 seconds, but almost certainly could be improved.
 */
void loop() {
  lineFollowerInterface.readLineFollower();
  lineFollowerInterface.findLine();
  lineFollowerInterface.computeAsterisks();
  pid.buttonPress(one.readButton());
  pid.printScreen();
  pid.runMotors(lineFollowerInterface.getLinePotential());
}
```
{{ site.data.alerts.end }}