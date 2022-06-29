# Turn and Push
Turn and Push is a simple way for a robot to navigate its environment.

Variations of this have been adapted for many robots, including space vehicles and the Roomba vacuum cleaning robot.

## Grey Walter's Tortoises

Grey Walter was a neuroscientist who developed a two robots called **tortoises**  to demonstrate that a small number of brain cells could perform complex behaviors.

His robot had two motors and a photo sensor. One motor drove forward and backward. The other turned like a steering wheel in a car, attached to the photo sensor. The robot would spiral until it saw light, then lock onto that light signal. All of the *AI* was controlled by a few transistors.

![Tortoise](img/tortoise.png)

By engineering the robot to turn its steering column towards a light source, the tortoise was said to "like" light. With getting close to the light as its goal, the robot would turn its steering column.

However, if an obstacle blocked the robot's path, with only the light sensor to guide it, the robot would become stuck, and never reach the light.

On the outside of the tortoise was a plastic shell. This was attached to a bump sensor. When bumped, the robot would do a very simple behavior. It would turn its steering column slightly to the left, and then back up. It did this on a timer. This behavior is called "turn and push."

By turning and pushing, the robot would eventually make its way around the obstacle, and to the light.

![Turn and Push](img/turn_and_push.png)

The Roomba does something similar as it vacuums. When its bump sensor is hit, it turns and begins its wandering behavior again.

## Challenge 5

Following light is not part of this challenge

- Start with the "empty" program.
- Make the robot move forward.
- When the obstacle sensor is triggered, rather than stopping the robot, make it go in reverse and to one side (you pick) for a moment. Use the `delay` function to regulate how long it does this.

If your program is successful, when encountering a wall, it should eventually turn so as to avoid hitting the wall, rather than becoming stuck! We will test the success of your robot by putting it into a pen with a wall. If the robot can get to the other side, you have passed the Turn & Push Challenge, and receive all of the bragging rights associated therewith.


{{ site.data.alerts.note }}
- Please flip your cup to red to indicate that you're ready to test your robot.
- Staff: Take the campers to the L-Shaped box on the Bridge. The robot should move from one "leg" of the box to the other by turning and pushing.
{{ site.data.alerts.end }}

{{+}}Challenge 5, 5{{+}}

{{-}}The Line Follower, in_person/robot_line_follower.md, Next{{-}}