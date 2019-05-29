# CarND PID Controller

## Overview
The aim of this project is to implement a PID controller in C++ to maneuver a vehicle around the track in the Udacity's car simulator! The simulator provides the cross track error (CTE) and the velocity (mph) then the code reads these values and calculates apropriate steering angle.

## Rubik

## Compilation
The code compiles without any errors! There was no need to modify `CMakeLists.txt` file.

## Implementation
The control algorithm used in this project follows the same techniques tought in the classroom.

## Refleciton
The parameters were chosen carefully to drive the car within the bounderies. In this project only P and D components of PID are used. Since there is no drift in the steering angle, the car was able to maneuver as desired without the I component.

__P Component__ is set to `0.1` which I found working perfectly for our car. The constant `Kp` is strong enough to bring our car back into the middle of the road quickly and smooth enough to reduces wobbles.

__D Component__ is set to `1.5`. I found differential component to be extremely useful for our car. Once I introduced D component the wobbles caused by P component were reduced to a greater extent. And now the car did not run outside the bounderies.

The hyperparameters were chosen manually based on trial and error method. I started experimenting with `Kp` with initial value 1, but found out that the turns were very aggresive. Then gradually decreased `Kp` untill some extend where I felt the steering was not very aggresive. At this point the car still was wobbling bit more than the desired.

As suggested in the classrom the swings of `P` controller could be reduced adding 'D' controller to it. Initially `Kd` was set to 1 and it worked pretty well. The car was wobbling lesser compared to earlier. Gradually increased `Kd` until the car was able to drive the track without overshooting the road, at this point the `Kd` was 1.5 .

Here are the final hyperparameters which worked well for me
```
Kp = 0.1
Ki = 0.0
Kd = 1.5
```

## Simulation
The car drives the entire track without running out of the driveable portion. The PID controller found to be very helpful to maneuver the car.
