# Pick-Place
In this task we use the defined locations mentioned in the exercises to pick and place the given object. In
the first part we grasp the object on the conveyor which is not moving while in the second part the
conveyor is moving. For this exercise we use the RX90.
We use Val II programming for the industrial robots.

We initialize first the variables for the inputs and the outputs, where inputs are related to sensors to
detect the object on the conveyor, whilst outputs are related to control the movement of the conveyor.
The numbers for the input and outputs are given in the exercise. Then we load the desired tool which is a
succion pad in this case. It is important to load the desired end-effector file as the frame of them may be
defined differently which can cause a crash.
At the first step the program wait till any objects are detected at the defined locations. This is handled
synchronously as it can be seen, because there is no point to execute the rest part of the program if there
is no object there. The other possibility could be that, we use asynchronous mode and we wait till the
signal comes and call a subroutine but in that case all of our code must be written in a subroutine which
is not a good idea.
After the object is detected, we approach the object and as we are close to it, we use moves which is a
translation along the Z axis. Then the closei command is used, which is a synchronous command as we
must wait till the previous motion instruction finished to be able to pick up the object.
Then we depart from the position and put the object on the conveyor at the predefined location then the
conveyor is started by the robot. First the object reaches the second sensor and after by changing the
direction of the conveyor it reaches also the first sensor at which we stop the conveyor. This is the grasp
location where the robot grasp the object with the command closei again. Then the robot moves to the
destination position with the object. Here to release the object we also use synchronous command openi.
Then the robot returns to a waiting position.
