# Design

Overview of design concepts of robots. Various use case that are considered.

## Use Case 1: Calibrate

Calibration is used to get critical information for training,  this task sets initial variables
specific to the robot, such as velocity over a given displacement.  Calibration should be performed
on the mid power range of the drone under ideal conditions. 

![Use Case 1 - calibration](/asserts/calibrate.jpg)

## Use Case 2: Training Mode

Once calibration has been performed, and initial variables such as velocity, and turning circle
have been added to drone internal configuration, then training needs to begin.

For training waypoints, along with corresponding labels, and sensor information are pushed through 
using an external device known as the personal trainer (PT).  The PT will replicate corresponding 
sensor information.

Training is performed by:

* Given a series of waypoints, along with labels corresponding to expected outputs. Train neural networks.
* This will iterate until training data reaches the desired results.

![Use Case 2 - training](/asserts/training.jpg)

## Use Case 3: Manual Flight

After robot has been calibrated, and trained.  It can be manually flown. For manual flight:
* a waypoint is sent to the robot;
* waypoint is evaluated by AI Engine, which can change direction based on results;
* results are saved to black box
* status is sent back to client.

![Use Case 3 - training](/asserts/man_flight.jpg)

## Use Case 4: Set Flight Path

* After robot has been calibrated and trained.  Paths can be set using [SET_PATH](/docs/developer/commands/msp8.md)
* Fat Controller Mapper adds each way-point to queue, in order.
* [MSP_MOTOR](/docs/developer/commands/msp104.md) are created and sent to AI handler
* Using [MSP_SENSOR](/docs/developer/commands/mspXX.md) commands, the current state of sensors is returned.
* [MSP_MOTOR](/docs/developer/commands/msp104.md) is sent to d-env, which is then returned to UI.

![Use Case 4 - training](/asserts/set_path.jpg)

