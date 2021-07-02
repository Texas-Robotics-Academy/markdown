---
title: "Maze Solving"
tags: [c++ programming]
keywords: maze algorithm
sidebar: tutorials
permalink: maze_solving.html
---

```
#include <BnrOneA.h>   // Bot'n Roll ONE A library
#include <EEPROM.h>    // EEPROM reading and writing
#include <SPI.h>       // SPI communication library required by BnrOne.cpp
BnrOneA one;           // declaration of object variable to control the Bot'n Roll ONE A

//constants definitions
#define SSPIN  2    //Slave Select (SS) pin for SPI communication
#define LEFT -1
#define DEAD_END 3
#define STRAIGHT 4
```

These are all the ways that the robot can opt to move. I made a function that determines when to do these things. Note that the robot never really turns right - the case for a uturn is the same as a right turn because of the left-hand rule.

```

#define Vtrans 250 //Line follower limit between white and black
#define DELAY 320

float batmin=10.5; // safety voltage for discharging the battery
int vel=30;
int prev_error=0;
```

`Vtrans` and `vel` were both set by us this time. We basically just messed around with the numbers until the robot was properly detecting intersections and operating in the maze properly.

```

void setup()
{  
  Serial.begin(57600);     // sets baud rate to 57600bps for printing values at serial monitor.
  one.spiConnect(SSPIN);   // starts the SPI communication module   
  one.stop();              // stop motors
  one.minBat(batmin);      // safety voltage for discharging the battery
  delay(1000);
}

void loop()
{  
  int dir = findTurn();
```

`findTurn()` determines whether the robot is going to turn left, make a uturn, or go straight. More on that later.

```

  if(dir != STRAIGHT){
    one.move(vel,vel);
    delay(100);

```

For all of the turns, we have the car drive forwards a little bit. This is due to the fact that in cross intersections, the robot was prematurely thinking it was completing the turns.

```

    if(one.readAdc(0) > Vtrans && one.readAdc(1) > Vtrans && one.readAdc(2) > Vtrans && one.readAdc(3) > Vtrans && one.readAdc(4) > Vtrans && one.readAdc(5) > Vtrans && one.readAdc(6) > Vtrans && one.readAdc(7)){
      one.lcd2("END");
      one.brake(vel,vel);
      while(true); //stops the robot

```

This is how we're detecting the end of the maze. If any of the non-middle sensors are above the threshold, the car drives forwards, and this check happens. The conditional there will only be true if every single sensor is above the threshold, which should only happen when there is a solid black line across the entire sensor. This would also happen at intersections - but the movement forwards prevents this check from stopping the robot at normal intersections.

The `while(true)` was the first thing I thought of for stopping the robot, since `loop()` is always run.

```

    }
    if(dir == LEFT){
      one.lcd1("LEFT");
      turn(LEFT);
```

Technically the turn function will only take in `LEFT` now, but I originally had it in mind that one should be able to specify left or right for their turn.

```

    } else if(dir == DEAD_END){
      one.lcd1("DEAD END");
      uturn();

    }
}
```

There is no right turn case. If we don't turn left and we don't go straight, we make a uturn. However, `uturn()` just has the car turn right until the middle two sensors register a line, which can result in a 90 degree right turn where applicable.

```

  int line=readLine();
  double k=0.45;//Linear gain to control motor speed

  double velM1=(double)vel+((double)line*k);
  double velM2=(double)vel-((double)line*k);  
  one.move((int)velM1,(int)velM2);


}

```

This part is just the line following code. I figure since the turns might not be perfect, its best to keep using the line following code to ensure the robot stays straight on the line.

```

void uturn(){
  while(one.readAdc(4) < Vtrans && one.readAdc(3) < Vtrans){
    one.move(vel,-vel);
  }
}

```

Here's the uturn function. All it does is keep turning right until one of the middle two sensors registers a black line.

```
void turn(int direction){
  if(direction != RIGHT && direction != LEFT){
    one.lcd1("ERROR INVALID TURN DIRECTION");
    return;
  }

  one.move(-vel,vel);
  delay(DELAY);
  while(one.readAdc(4) < Vtrans && one.readAdc(3) < Vtrans){
    one.move(vel*direction,-vel*direction);
  }
}

```

Here's the left turn function. It can do left or right, but I only call it to turn left. It's doing the same thing as the uturn function, but with a little more flexibility.

```

int findTurn(){
  if(one.readAdc(0) > Vtrans && one.readAdc(1) > Vtrans)
    return LEFT;

```

  This statement checks to see if we can turn left. Since we're operating on the left-hand rule, we should always turn left if we can, so this has to be the first check.

```

  else if(one.readAdc(7) < Vtrans && one.readAdc(6) < Vtrans && one.readAdc(5) < Vtrans && one.readAdc(4) < Vtrans && one.readAdc(3) < Vtrans && one.readAdc(2) < Vtrans && one.readAdc(1) < Vtrans && one.readAdc(0) < Vtrans)
    return DEAD_END;  
  else
    return STRAIGHT;

}
```

If none of the sensors are registering above the threshold, we turn right until we something is registered. You'll notice that this accounts for both the right turn and uturn case. This is because of the fact that we're always moving forwards. Since going straight is prioritized over turning right, we can end up in the following scenario:

- L shaped intersection where you can only turn RIGHT
- findTurn returns straight, since you can't turn left but some of the sensors are registering above the threshold
- car keeps going forwards
- findTurn is called again
- IR sensors are now reading nothing, since the car went forward even though it could only turn RIGHT. DEAD_END is returned by findTurn
- Car keeps turning right until a middle sensor registers above the threshold
- Car has actually turned 90 degrees to the right, since there is a line There

```

int readLine()
{
    int lineValue=0;
    int sensorCount=0;
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
    if(sensorCount>2)
        lineValue=-1;
    else if(sensorCount>0)
        lineValue=lineValue/sensorCount;
    return lineValue;
}

```

This is still the same as the line follower code. Nothing new here.

Your next task is to create a maze-solving algorithm. The maze in which the robots will be tested is *simply connected*, which means that all of its walls will be connected together. In order to traverse the maze, the robot will be traveling along the line, so you will need to expand on the line follower program you created in the previous step.

## Develop a maze solving rule
You want your robot to be able to solve any maze we give it, so before you start programming, you need to develop a general rule for our robot to follow that will always lead it to the end of the maze. This will give you a good sense of what you are trying to develop.
Look at the example maze below, and use it to help you develop the rule you want your robot to follow. Whatever rule you do create, it probably will not be the fastest way through the maze, but it should eventually get through the maze.

<img src="images/sample_maze.svg" alt="Sample maze" class="maze-image" />

## Design of the Maze

The maze is built with black lines so you can build off of your line follower code. The maze will have both T-intesections and four way intersections. In these cases, which way should the robot go first? Try to make the robot turn in the same direction, whichever you choose, every time it is faced with this choice. The end of the maze will be marked by a black rectangle, at which point the robot must stop.

## Task 10

Once you have developed a general rule, it's time to start programming and then testing!

{% include callout_red_cup.html task="9.2" comment="Please flip your cup to red. A camp staff member will bring you to a maze to test your robot with. Feel free to run your robot at your desk while you wait, but try not to create chaos in doing so." %}

{% include note.html content="Camp Staff: Bring the group to one of the mazes and ensure that the robot is able to complete the maze."%}

Finally, let's attach some [LEDs](led.html) to the robot.
