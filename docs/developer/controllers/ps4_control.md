# PS4 Controller 

PS for controller is used to control the drone with the following configuration, 
in manual flight mode.

![PS 4 controller diagram](/asserts/ps4-controller-vector-png-4.jpg)

| Controller   | Function        | Range   | C++ type | Java Type |
|--------------|-----------------|---------|----------| --------- |
| Left X Axis  | roll            | -1:1    | int8_t   | short     |
| Left Y Axis  | throttle/ pitch | 0:1000  | uint16_t | integer   |
| Right X Axis | yaw             | -1:1    | int8_t   | short     |
| Right Y Axis | pitch           | -1:1    | int8_t   | short     |   


- [see msp104](../commands/msp104.md)