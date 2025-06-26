# Solution - Exercise 8: Turn & Push

## Exercise 8.1:
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

class TurnAndPush {
public:
  TurnAndPush() {}
  
  void reactToObstacles() {
    byte threshold = 10;
    byte leftO = one.readLeftRangeSensor();
    byte rightO = one.readRightRangeSensor();
    byte obstacleDetection = 0;
    if(leftO > threshold) {
      if(rightO > threshold) {
        obstacleDetection = 3;
      } else {
        obstacleDetection = 1;      
      }
    } else if(rightO > threshold) {
      obstacleDetection = 2;    
    }  
    
    switch(obstacleDetection) {
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
  }
};

TurnAndPush turnAndPush;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
  one.obstacleSensorsEmitters(true);
}

void loop() {
//  menu.buttonPress(one.readButton());
//  menu.runMotors();
//  menu.printMenu();
  turnAndPush.reactToObstacles();
}
```
{{ site.data.alerts.end }}

## Exercise 8.2:
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

class MotorMenu {
public:
  MotorMenu() : _lastButton(0), _whichItem(0), _forwardSpeed(30), _backLeft(-45), _backRight(-30), _backupTime(250) {}

  void buttonPress(byte button) {
    switch(button) {
      case 0:
        break;
      case 1:
        if(_lastButton != 1) {
          _whichItem++;
        }
        if(_whichItem == 4) {
          _whichItem = 0;
        }
        break;
      case 2:
        switch(_whichItem) {
          case 0:
            _forwardSpeed++;
            break;
          case 1:
            _backupTime++;
            break;
          case 2:
            _backLeft++;
            break;
          case 3:
            _backRight++;
            break;
        }
        break;
      case 3:
        switch(_whichItem) {
          case 0:
            _forwardSpeed--;
            break;
          case 1:
            _backupTime--;
            break;
          case 2:
            _backLeft--;
            break;
          case 3:
            _backRight--;
            break;
        }
        break;
    }

    if(_backupTime < 0) {
      _backupTime = 0;
    }

    if(_forwardSpeed < -100) {
      _forwardSpeed = -100;
    }

    if(_backLeft < -100) {
      _backLeft = -100;
    }

    if(_backRight < -100) {
      _backRight = -100;
    }

    if(_forwardSpeed > 100) {
      _forwardSpeed = 100;
    }

    if(_backLeft > 100) {
      _backLeft = 100;
    }

    if(_backRight > 100) {
      _backRight = 100;
    }
    
    _lastButton = button;
  }

  void printMenu() {
    String f = _whichItem == 0 ? ("*F: " + String(_forwardSpeed) + " ") : ("F: " + String(_forwardSpeed) + " ");
    String d = _whichItem == 1 ? ("*D: " + String(_backupTime) + " ") : ("D: " + String(_backupTime) + " ");
    String bl = _whichItem == 2 ? ("*BL: " + String(_backLeft) + " ") : ("BL: " + String(_backLeft) + " ");
    String br = _whichItem == 3 ? ("*BR: " + String(_backRight) + " ") : ("BR: " + String(_backRight) + " ");

    one.lcd1(f + d);
    one.lcd2(bl + br);
  }

  void forward() {
    one.move(_forwardSpeed, _forwardSpeed);
  }

  void backwardTurn() {
    one.move(_backLeft, _backRight);
    delay(_backupTime);
  }

protected:
  byte _lastButton;
  int _whichItem;
  int _forwardSpeed, _backLeft, _backRight, _backupTime;
};

MotorMenu menu;

class TurnAndPush {
public:
  TurnAndPush() {
    
  }

  void reactToObstacles() {
    byte threshold = 10;
    byte leftO = one.readLeftRangeSensor();
    byte rightO = one.readRightRangeSensor();
    byte obstacleDetection = 0;
    if(leftO > threshold) {
      if(rightO > threshold) {
        obstacleDetection = 3;
      } else {
        obstacleDetection = 1;      
      }
    } else if(rightO > threshold) {
      obstacleDetection = 2;    
    }  

//    switch(obstacleDetection) {
//      case 0:
//        one.lcd1("No obstacle");
//        break;
//      case 1:
//        one.lcd1("Left");
//        break;
//      case 2:
//        one.lcd1("Right");
//        break;
//      case 3:
//        one.lcd1("Both");
//        break;
//    }
  }
};

TurnAndPush turnAndPush;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  menu.buttonPress(one.readButton());
//  menu.runMotors();
  menu.printMenu();
  turnAndPush.reactToObstacles();
}
```
{{ site.data.alerts.end }}

## Exercise 8.3:
{{ site.data.alerts.callout_code_div }}
```
#include <BnrOneAPlus.h>
#include <SPI.h>

#define SSPIN 2

BnrOneAPlus one;

class MotorMenu {
public:
  MotorMenu() : _lastButton(0), _whichItem(0), _forwardSpeed(30), _backLeft(-45), _backRight(-30), _backupTime(250) {}

  void buttonPress(byte button) {
    switch(button) {
      case 0:
        break;
      case 1:
        if(_lastButton != 1) {
          _whichItem++;
        }
        if(_whichItem == 4) {
          _whichItem = 0;
        }
        break;
      case 2:
        switch(_whichItem) {
          case 0:
            _forwardSpeed++;
            break;
          case 1:
            _backupTime++;
            break;
          case 2:
            _backLeft++;
            break;
          case 3:
            _backRight++;
            break;
        }
        break;
      case 3:
        switch(_whichItem) {
          case 0:
            _forwardSpeed--;
            break;
          case 1:
            _backupTime--;
            break;
          case 2:
            _backLeft--;
            break;
          case 3:
            _backRight--;
            break;
        }
        break;
    }

    if(_backupTime < 0) {
      _backupTime = 0;
    }

    if(_forwardSpeed < -100) {
      _forwardSpeed = -100;
    }

    if(_backLeft < -100) {
      _backLeft = -100;
    }

    if(_backRight < -100) {
      _backRight = -100;
    }

    if(_forwardSpeed > 100) {
      _forwardSpeed = 100;
    }

    if(_backLeft > 100) {
      _backLeft = 100;
    }

    if(_backRight > 100) {
      _backRight = 100;
    }
    
    _lastButton = button;
  }

  void printMenu() {
    String f = _whichItem == 0 ? ("*F: " + String(_forwardSpeed) + " ") : ("F: " + String(_forwardSpeed) + " ");
    String d = _whichItem == 1 ? ("*D: " + String(_backupTime) + " ") : ("D: " + String(_backupTime) + " ");
    String bl = _whichItem == 2 ? ("*BL: " + String(_backLeft) + " ") : ("BL: " + String(_backLeft) + " ");
    String br = _whichItem == 3 ? ("*BR: " + String(_backRight) + " ") : ("BR: " + String(_backRight) + " ");

    one.lcd1(f + d);
    one.lcd2(bl + br);
  }

  void forward() {
    one.move(_forwardSpeed, _forwardSpeed);
  }

  void backwardTurn() {
    one.move(_backLeft, _backRight);
    delay(_backupTime);
  }

protected:
  byte _lastButton;
  int _whichItem;
  int _forwardSpeed, _backLeft, _backRight, _backupTime;
};

MotorMenu menu;

class TurnAndPush {
public:
  TurnAndPush() {
    
  }

  void reactToObstacles() {
    byte threshold = 10;
    byte leftO = one.readLeftRangeSensor();
    byte rightO = one.readRightRangeSensor();
    byte obstacleDetection = 0;
    if(leftO > threshold) {
      if(rightO > threshold) {
        obstacleDetection = 3;
      } else {
        obstacleDetection = 1;      
      }
    } else if(rightO > threshold) {
      obstacleDetection = 2;    
    }  


    if(obstacleDetection == 0) {
      menu.forward();
    } else {
      menu.backwardTurn();
    }
//    switch(obstacleDetection) {
//      case 0:
//        one.lcd1("No obstacle");
//        break;
//      case 1:
//        one.lcd1("Left");
//        break;
//      case 2:
//        one.lcd1("Right");
//        break;
//      case 3:
//        one.lcd1("Both");
//        break;
//    }
  }
};

TurnAndPush turnAndPush;

void setup() {
  Serial.begin(115200);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  menu.buttonPress(one.readButton());
//  menu.runMotors();
  menu.printMenu();
  turnAndPush.reactToObstacles();
}
```
{{ site.data.alerts.end }}