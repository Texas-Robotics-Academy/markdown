| Function | What it does |
|----------|--------------|
|```one.lcd1(String string)```| Prints text on the first line of the LCD  |
|```one.lcd2(String string)```| Prints text on the second line of the LCD |
|```Serial.println(String string)```| Prints on the serial port  |
|```delay(int milliseconds)```| Pauses the program for millisconds  |
|```one.setLed(bool state)```| Turns the LED on or off based on "state"  |
|```one.readLeftRangeSensor()```| Returns how far (0-25) the nearest object is from the left sensor  |
|```one.readRightRangeSensor()```| Returns how far (0-25) the nearest object is from the right sensor  |
|```one.readObstacleSensors()```| ~~0 - Neither sensor. 1 - Left sensor. 2 - Right sensor. 3 - Both sensors.~~ Doesn't work. |
|```one.obstacleSensorsEmitters(const bool state)```| Turns on and off the obstacleSensorEmitters |
|```one.readButton()```| 0 - No button. 1 - Button 1. 2 - Button 2. 3 - Button 3.  |
|```one.move(int left_speed, int right_speed)```| -100 to -100 for the left and right motor. Zero is stopped. Negative numbers mean spin backwards. |