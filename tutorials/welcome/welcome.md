---
title: "Welcome!"
tags: [welcome]
keywords: welcome
sidebar: tutorials
permalink: welcome.html
---

First, welcome to camp! You should be seated at a workstation next to your partner. If you have not yet taken the time to introduce yourselves to each other, spend a minute or two to get to know each other. You'll be working together all week.

This week you will go through a mostly self-paced tutorial on how to program your robot. Your tutorial will be interspersed with instruction, challenges and activities on the robot, and outside activities like visits to tech companies and lectures from scientists working in robotics. We have done everything that we could think of to pack as much fun as possible into this week.

First, a few preliminaries.

## Cups

You have received a pair of cups which are taped to each other.

{% include note.html content="Actually, you didn't. We accidentally locked them in the workshop that we'll be in tomorrow. For today, just raise your hand when you need help." %}

One is red. One is blue. At this time, you should place your pair of cups on top of the computer monitor in front of you, with the blue cup facing up.

* When the red cup is facing upward, it means:

   * I need help.
 
   * I have completed something, and am ready for camp staff to mark my progress.

* When the blue cup is facing upward, it means:

  * Neither of those two conditions are currently true.

{% include callout_blue_cup.html task="Initial Setup" comment="If you need help, you will indicate such by flipping it to red from now on. Once you have completed this, keep going through the tutorial." %}


At this point, please **actually** flip your cup to blue, and start using the cups as needed. 

## Synchronizing Groups

There are some activities that we will do as one big group. For instance, sections of the tutorial are accompanied by brief lectures or group activities. Sections that are done as a group will be marked with a yellow box to indicate that you should wait to synchronize with the other campers.

{% include callout_synchronize.html  comment="This is just to show you what it looks like. Keep going." %}

## Tips

Sometimes we need to tell you something tangential to the line of thought of the tutorial, but important to point out. Tips look like this.

{% include tip.html content="Don't get distracted by the tips. They're intended to help you, not side-track you." %}

## Command Line Instructions

Sometimes we just want you to type something into the computer and we just tell you what it is. You should literally copy-paste these commands when you see a box like this. The commands below are just an example, and are harmless, but not productive.

{{ site.data.alerts.terminal_commands }}
cd
ls
pwd
{{ site.data.alerts.terminal_commands_end }}

## Keeping Track of your Robot

Every team in this camp will have a virtually identical robot. To tell them apart, we will give you sticky notes and boxes to store them in.

When you come back here with your robots, you will write you team number onto the sticky note and stick it to the top of your robot. Your robot and its parts should always stay in its box. Don't worry about this at this time.

## Tutorials

This camp comprises a series of mostly self-paced tutorials. Each tutorial is documented on this website. You can navigate the tutorials using the navigation bar on the left. You can always return to the top of the website by clicking on the "Texas RoboCamp" logo in the upper left-hand corner.

## Where You Sit

Every time you enter the lab, your assigned seat will change. This is so we can group campers together who are working on similar activities, so we can better help you as a group. Please make sure to look for the sign indicating where you should sit every time you enter into the lab, and sit in the corresponding area.

## Challenges and Activities

Tutorials prepare you for programming challenges and activities by providing you with the tools that you need in order to complete the task.

Once you have learned enough skills to solve a programming challenge or take part in an activity, the tutorial will present you with an activity or challenge to participate in.

Because the week is self-paced, feel free to take longer on activities and challenges that you really enjoy. Be wary that some later activities and challenges build on skills that you develop in earlier ones, so make sure that you *do* complete each activity.

There are bonus activities at the end of the camp, which invite you to become creative in the way that you use what you have learned or improve the performance of something that you have written to try to improve the performance of your robot.

## Tracking your Progress

### Progress Logs

Your progress will be logged in a progress log. You're about to see what your first progress log looks like.

{{ site.data.alerts.terminal_commands }}
cd
mkdir forms
cd forms
wget https://github.com/texas-robocamp/texas-robocamp.github.io/raw/master/forms/camper_checklist_1.pdf
wget https://github.com/texas-robocamp/texas-robocamp.github.io/raw/master/forms/pair_programming_log.pdf
lpr -Plw303 camper_checklist_1.pdf
lpr -Plw303 pair_programming_log.pdf
{{ site.data.alerts.terminal_commands_end }}

- Go get your checklist and pair programming log off of printer 303, which us under the television monitor by the lounge area.
- When you have your box, you will get some tape from a counselor to affix it to the top of your box.

{{ site.data.alerts.tip }}
We don't want you printing things unless instructed to by the camp. Please refrain from printing things using `lpr` unless either instructed to do so or unless you have previously obtained permission from a counselor to do so.
{{ site.data.alerts.end }}

### Pair Programming

Pair programming is a technique by which two people work together to solve a programming problem. In this camp, you and your partner will work together to program your robot. You will keep each other on task and motivated. You will talk through coding issues when you do not know how to solve them.

You should spend roughly equal time "driving," typing at the computer. To help you keep track, we have given you a pair programming log.

![Programming log](images/programming_log.png)

Fill it out as follows:

* Put your team number next to the text "Team Number."

* Put your log number in the "log number" box. This is there in case you fill up more than one sheet.

  * C++, as well as most programming languages begins indexing at Zero. So, your first log should be 0 in order to remind you of this, not 1!

* Put the person on the top of your team sheet as Camper 0, and the one at the bottom as Camper 1.

  * These numbers do not indicate rank or seniority, nor do they indicate that either of you is a zero or number one. They track your hours.

* When beginning to work on an exercise or tutorial, or any time that you are solving a programming problem, elect a "driver" who will be operating the computer. Write their number into the next line under "Driver," and mark the current date, and start time.

* When switching drivers, mark the "stop" time. Compute the amount of time that has elapsed and put that into the corresponding box under the number of the current driver. Then, fill out the next line appropriately for the new driver.

* When you reach the Subtotal boxes, add up the amount of time that each of you has spent driving.

* Try to change drivers every 30 minutes.

### Red Cups to Mark Progress

At designated points through your progress on this website, you will be asked to notify camp staff of your progress.

It will look like this:

{% include callout_red_cup.html task="[Tutorial 1]" %}

At this point, please **actually** flip your cup to red.

## Next Step

Proceed to ["Using Linux."](/using_linux.html)
