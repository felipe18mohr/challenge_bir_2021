# BIR  Challenge 2021
![challenge](resources/challenge.png)

Challenge for act as undergraduate intern in the Robotics and Autonomous Systems Laboratory, in SENAI CIMATEC, 2021.

## The repository
**Table of Contents**
- [BIR  Challenge 2021](#bir--challenge-2021)
  * [The repository](#the-repository)
  * [The Challenge](#the-challenge)
    + [Robot](#robot)
    + [Sensors](#sensors)
    + [Controller](#controller)
  * [Results](#results)

## The Challenge

### Robot

### Sensors
The Pioneer P3dx, used in the challenge, has 16 Distance Sensors attached. They will be used to get information from the environment, so that it is possible to avoid obstacles.

For this challenge, the robot mission is to reach a region illuminated by a lamp.  For that, a Light Sensor was added to the robot, so that it is possible to identify when that region was reached.

### Controller
The controller used for this challenge is based on a very simplistic State Machine, wich can be  seen in the diagram below.
![state_machine](resources/state_machine.png)

It has four states: 
- **FORWARD:** Moves forward, and begins to turn in either direction when an obstacle is close enough, to avoid it, changing the State to  LEFT or RIGHT;
- **LEFT:** Turn left until no more obstacle are in sight;
- **RIGHT:** Turn right until no more obstacle are in sight;
- **FINISH:** When the robot reaches the goal, stop it and print the information on the screen.

The transitions are explained below:
- **Transition 1 (\_T1\_):** Right Wheel Weight greater then the threshold;
	- FORWARD  :arrow_right:  LEFT
- **Transition 2 (\_T2\_):** Left Wheel Weight greater then the threshold. Transition 1 has more priority;
	- FORWARD :arrow_right: RIGHT
- **Transition 3 (\_T3\_):** Left AND Right Wheels Weight smaller then the threshold;
	- LEFT :arrow_right: FORWARD
	- RIGHT :arrow_right: FORWARD
- **Transition 4 (\_T4\_):** Luminosity read by the Light Sensor is high enough.
	- FORWARD :arrow_right: FINISH
	- LEFT :arrow_right: FINISH
	- RIGHT :arrow_right: FINISH

## Results
