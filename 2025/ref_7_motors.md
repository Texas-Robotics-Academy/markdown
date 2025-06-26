# Solution - Exercise 7: Controlling the Motors

## Exercise 7.1:
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

class MotorMenu {
public:
  MotorMenu() {
    _lastButton = 0;
    _whichMotor = 0;
  }

  void buttonPress(byte button) {
    switch(button) {
      case 0:
        break;
      case 1: 
        if(_lastButton != button) {
          _whichMotor = !_whichMotor;
        }
        break;
      case 2:
        if(_whichMotor) {
          _rightSpeed++;
          if(_rightSpeed > 100) {
            _rightSpeed = 100;
          }
        } else {
          _leftSpeed++;
          if(_leftSpeed > 100) {
            _leftSpeed = 100;
          }
        }
        break;
      case 3:
        if(_whichMotor) {
          _rightSpeed--;
          if(_rightSpeed < -100) {
            _rightSpeed = -100;
          }
        } else {
          _leftSpeed++;
          if(_leftSpeed < 100) {
            _leftSpeed = -100;
          }
        }
        break;
    }
    _lastButton = button;
  }

  void runMotors() {
    one.move(_leftSpeed, _rightSpeed);
  }

  void printMenu() {
    String lineOne = String(_leftSpeed) + "  " + String(_rightSpeed);
    one.lcd1(lineOne);
    if(_whichMotor) {
      one.lcd2("--->");
    } else {
      one.lcd2("<---");
    }
  }

protected:
  byte _lastButton;
  bool _whichMotor;
  int _leftSpeed, _rightSpeed;
};

MotorMenu menu;

int counter = 0;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  menu.buttonPress(one.readButton());
  menu.runMotors();
  menu.printMenu();
}
```
{{ site.data.alerts.end }}