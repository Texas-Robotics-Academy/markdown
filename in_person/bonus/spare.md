

```
one.move(speedL,speedR);
```

The `move` function takes in two parameters, `speedL` and `speedR`, and moves the left and right motors at the speeds specified. This function takes in values ranging from -100 to 100, where -100 is the maximum speed in reverse, and 100 corresponds to the maximum speed in the forward direction, and 0 stops the motors.

{{ site.data.alerts.tip }}
You can turn the robot by moving the motors at different speeds. 
<ul>
<li>-100, 100 would turn the robot as hard to the left as possible</li>
<li>100, 50, would turn the robot less sharply to the right, navigating the robot in a circle..</li>
</ul>
{{ site.data.alerts.end }}


## Moving the Car

The remaining functions from the obstacle_avoidance code that we haven't talked about all involve controlling the movement of the car.

```
one.move(50,50);
```

The `move()` function takes two arguments: speedL and speedR. These values define the speed of each motor, which ranges from -100 to 100. -100 corresponds to the max speed in reverse, and 100 corresponds to the max speed in the forward direction. An input of 0 stops the motor.

```
one.brake(50,50);
```

The `brake()` function also takes two arguments: torqueL and torqueR. These values define the braking power of each motor, which ranges between 0 and 100. Zero corresponds to stopping without braking, whereas 100 corresponds to stopping with the maximum braking torque.

### Task 8.2
Now that you know how to make the car start and stop, let's test out these functions! Write a program that has the car drive forwards for 2 seconds, brakes, and repeats.

Before you write this program, however, you'll need to know about one more function, `void delay(milliseconds)`. This function returns no value, and has the program wait for a specified amount of milliseconds before executing the next line of code. So, if you wanted to wait 5 seconds before running the next line of code, you would do:

```
//Do something
delay(5000);
//Do something else
```


### Additional Functions

Technically, you now have all of the functions that you need in order to get the robot to avoid obstacles. However, there are some additional functions for the BnrOneA class that you may find useful. Remember that to call any of these functions, you have to type `one.functionName()`.

```
void stop()
```

This function cuts energy to both motors on the Bot'n'Roll, causing them to rotate freely until they stop. This is the same as calling `move(0,0)`

```
void led(state)
```

This function can set the LED on or off, depending on the state passed in. Passing in 0 turns the LED off, and passing in 1 turns the LED on.

## Beeping

The default behavior of the obstacle avoidance program is to turn away when the robot senses obstacles on one side, or back up when the robot senses obstacles on both sides. This is bad driving! The robot should tell us when it's about to turn or back up. The objective of your first robot program is signalling. We will let you decide how to signal. We suggest a beep for backing up, and lights for turning.

In order to make your car beep, you'll need two more functions, `tone(pin,frequency,duration)` and `noTone(pin)`.

The `tone(pin,frequency,duration)` function generates a square wave of the specified frequency on the specified pin. The `duration` parameter is optional. If you do not put a value for duration, the wave will continue until `noTone(pin)` is called. The pin you'll be using for sound is pin 9.

### Task 8.3
Now that you know how to produce sound on your car, write a program that makes the car beep for 5 seconds.



```
#define SSPIN  2    //Slave Select (SS) pin for SPI communication
#define M1  1       //Motor1
#define M2  2       //Motor2

#define Vtrans 300 //Line follower limit between white and black

float batmin=10.5; // safety voltage for discharging the battery
int vel=40;


void setup()
{  
  Serial.begin(57600);     // sets baud rate to 57600bps for printing values at serial monitor.
  one.spiConnect(SSPIN);   // starts the SPI communication module   
  one.stop();              // stop motors
  one.minBat(batmin);      // safety voltage for discharging the battery
  delay(1000);
}

```

None of the setup stuff is special for this program. `vel` is used later, and was a hardcoded value provided by Bnr. I suspect it could be made to go faster.


```
void loop()
{
  int line=readLine();

```

From a high-level perspective, all readLine does is return a value from -100 to 100 that represents where the line is, according to the sensor. I'll explain it more when I get to that part in the code.

```  
  double k=0.45;//Linear gain to control motor speed <> Ganho linear para controlar a velocidade dos motores

```

This value came directly from the Bnr code, and is the scaling factor for line. I assume they fine-tuned this parameter. It's worth noting that there might be a better number than this. The only constraint on the value for `k` is that `vel + line*k =< 100` and `vel - line*k >= -100`. Technically, none of the variables have to have any other contraints, but it seems intuitive to keep `-100 <= line <= 100`

```
  double velM1=(double)vel+((double)line*k);
  double velM2=(double)vel-((double)line*k);
  one.move((int)velM1,(int)velM2);

}
```

Here's where the actual proportional control is made. The only part about these lines that I haven't already mentioned that I think is important is that one of the values adds `line*k` whereas the other subtracts. Since the car is turning, one value has to be subtracted while the other needs to be added to ensure that the car turns. Technically it doesn't matter which is added and which is subtracted, but in the opposite case than what's written, the values being added to `lineValue` in `readLine()` will all need to have their signs flipped.

```
int readLine()
{
    int lineValue=0;
    int sensorCount=0;

```

`lineValue` is set to zero, since the default assumption is that the car is following the line.

```
    if(one.readAdc(0)>Vtrans) //Test Sensor1  <>  Testa o sensor1
      {                       
        lineValue-=100;
        sensorCount++;
      }
    if(one.readAdc(1)>Vtrans) //Test Sensor2  <>  Testa o sensor2
      {                       
        lineValue-=75;
        sensorCount++;
      }
    if(one.readAdc(2)>Vtrans)
      {
        lineValue-=50;
        sensorCount++;
      }
    if(one.readAdc(3)>Vtrans)
      {
        lineValue-=25;
        sensorCount++;
      }
    if(one.readAdc(4)>Vtrans)
      {
        lineValue+=25;
        sensorCount++;
      }
    if(one.readAdc(5)>Vtrans)
      {
        lineValue+=50;
        sensorCount++;
      }
    if(one.readAdc(6)>Vtrans)
      {
        lineValue+=75;
        sensorCount++;
      }
    if(one.readAdc(7)>Vtrans) //Test Sensor8  <>  Testa o sensor8
      {                       
        lineValue+=100;
        sensorCount++;
      }

```

Here's where all the sensors are evaluated. Due to how `velM1` and `velM2` are set, this function uses negative values to represent the line being towards the left, and positive values to represent the line being towards the right.

What the code is doing is checking to see which sensors are registering a dark line below them. The threshold value, `Vtrans`, was provided by Bnr, but other values may likely work.

The values being added to `lineValue` have the following idea in mind: the larger the value returned by readLine, the farther the robot needs to turn in order to get back on the line. I assume that the extreme values (-100, 100) were conjured up due to the limits on the `move()` function. From there, The number of sensors makes it such that incrementing by 25 makes the most sense. Since there is no middle sensor, there is no case that adds zero. Since the values being added to `lineValue` are opposites for opposite sensors, however, a line (no matter how thick) that is in the middle (or that is covering all of the sensors) will have `readLine()` return zero.

```
    if(sensorCount>0)
        lineValue=lineValue/sensorCount;
    return lineValue;
}
```

Finally, `lineValue` is divided by the number of sensors that registered above the threshold before being returned. This makes sense because if more than one sensor registers above the theshold, then the "center" of that line is technically between the two sensors. That is to say that if the two far left sensors registered above the threshold, we would not want to return -175, but rather 87.5



`lineValue` is originally set to zero, since the base assumption is that the car is driving straight on the line. From there, `readLine` goes through each sensor and checks to see if its above some threshold.

`readAdc(byte)` returns values from 0-1023. In their code, they specify 300 as the threshold for saying something is black vs white





### Binary Code

Oddly enough, now is a good time to discuss binary.

We all know that computers represent data as 1s and 0s, but what does that really mean? Well, it's about to become immediately relevant to your ability to program this robot.

Binary is called a numerical base.

Decimal is the base that we are used to, where there are 10 digits (0-9), and we add additional digits to make bigger numbers.

In binary, there are two digits (0 & 1), and we add additional digits to make bigger numbers.

Binary was chosen as the numerical system for computers because computers use transistors, which can be thought of as switches which only go on or off, to represent basically everything. Since a switch can only be on or off, this naturally maps to there being two values for each digit in the computer's number system. Hence binary.

Each switch, a 1 or 0 is called a bit.

8 bits make a byte.

{{ site.data.alerts.tip }}
<ul>
<li>If you have heard of 8-bit, 16-bit, 32-bit, or 64-bit computer architectures, this refers to the number of bits used to represent an integer and other basic things in the computer.</li>
<li>Notice that the lengths are all powers of two. This is no mistake. Using powers of two is typically more efficient when designing things for computers.</li>
</ul>
{{ site.data.alerts.end }}

We need to know a couple more things before we can understand binary. We need to quickly understand exponents.

Left-Hand-Side    | Equals
--------|-------------
2	| 2
2 * 2	    |4
2 * 2 * 2	| 8
2 * 2 * 2 * 2	| 16

We can also state these as exponents, which just means multiplying the number by itself as many times as is in the exponent.

Left-Hand-Side    | Exponent    | Equals
--------|-------------|-------------
2	| 2<sup>1</sup>	| 2
2 * 2	    | 2<sup>2</sup>	    |4
2 * 2 * 2	| 2<sup>3</sup>	| 8
2 * 2 * 2 * 2	| 2<sup>4</sup>	| 16

Okay, but here's one which will really blow your mind if you haven't seen it before.

 Exponent    | Equals
-------------|-------------
2<sup>0</sup>	| 1

{{ site.data.alerts.tip }}
Explaining this would really get the camp off-course, but if you are curious, you can learn more <a href="http://scienceline.ucsb.edu/getkey.php?key=2626">here</a>.
{{ site.data.alerts.end }}
