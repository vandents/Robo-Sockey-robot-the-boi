# Robo-Sockey-robot-the-boi

GVSU's Robo Sockey competition, a mix between soccer and hockey, is a semester long competition between all of the students that are enrolled in Introduction to Engineering II. Students were tasked with creating an Arduino robot from scratch that could navigate itself through obstacles without human assistance. Using a 6-foot-by-6-foot arena, teams have three minutes to compete with each other to deliver the most amount of balls into a goal. Teams of 4 were assigned at the beginning of the semester. In total, 40 teams competed in the competition.


My team's robot, named "The Boi", implemented many original design features. Our robot not only obtained first place, but also earned the Design Innovation Award.

How The Boi works:

The Boi navigates the course using 4 IR sensors, 5 IR recievers and 2 microswitches.

The rest of The Boi is composed of 2 6V motors, 6 AA batteries, a continuous servo, an H-Bridge, an Arduino Uno and a number of custom milled ABS plastic parts.

At the heart of The Boi's code is a state machine. The potential states are as follows: 
START - initial state, 
RANDOM - decides the next movement based on input from sensors, 
REVERSE - calls function to reverse robot and then decides a random turn to be performed, 
GOAL_FIND - implemented when robot has captured a ball, similar to RANDOM but acknowledges input from the IR recievers, 
TO_GOAL - once the goal is spotted this state is implemented to drive toward the goal, 
FIRE - reverse wheels and waterwheel to shoot out ball, 
ONE80 - 180 degree turn, 
LEFT_90 - 90 degree left turn, 
RIGHT_90 - 90 degree right turn, 
SLIGHT_L - slight left turn, 
SLIGHT_R - slight right turn

The Boi drives straight until it times out (5 seconds) or detects an obstacle/other robot with its IR or microswitch sensors. Upon obstacle detection, The Boi will reverse and execute a random turn.

The Boi has a "waterwheel" that continuously spins forward in hopes of gathering a ball. If The Boi detects that it has gathered a ball it will go into goal finding mode. When in goal finding mode it will continue with its normal random movement until it detects the IR beam mounted above the goal with its array of IR recievers. Once it detects the IR beam, The Boi will turn toward the goal and drive until it is underneath the goalpost. Once the upright facing IR sensors detect that it is under the goal, it will enter scoring mode where the  waterwheel servo reverses and the wheels reverse. After it has scored the ball it will go back to random movement.
