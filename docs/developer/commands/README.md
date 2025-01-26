# Ryder Robot Protocol (RRP)

Allows communication from client to drone, internally within drone for handlers, and between drone to micro-processor.

## Command Format

 | Attribute  | Description                                   | 
 |------------|-----------------------------------------------|
 | command    | instructs drone to perform an action          |
 | direction  | defines if the command is inbound or outobond |
 | payload    | series of attributes for command              |

## JSON format

Format for communication between to drone.

Example command.

```
{
      "command": "MSP_MOTOR,
      "paylad": {
          "roll": 0,
          "pitch": 0,
          "yaw": 0,
          "throttle": 500,
          "aux1: 0,
          "aux2: 0,
          "aux3: 0,
          "aux4: 0
      }
}
```

## Serial Protocol
```
<preamble>,<direction>,<size>,<command>,,<crc>
```

* preamble = the ASCII characters '$M'

* direction = the ASCII character '<' if to the drone or '>' if from the drone

* size = number of data bytes, binary. Can be zero as in the case of a data request to the MWC

* command = message_id as per the table below

* data = as per the table below. UINT16 values are LSB first.

* crc = XOR of <size>, <command> and each data byte into a zero'ed sum

## Commands


| command                 | message_id | drone only | description                     |
|-------------------------|------------|------------|---------------------------------|
| MSP_NONE                | 0          | N          | no command given                |
| MSP_MODE                | 1          | N          | changes drone mode              |
| MSP_ERROR               | 2          | N          | indicates an error has occurred |
| [MSP_SET_PATH](msp8.md) | 8          | N          | sets waypoints for done         |
| MSP_STATUS              | 101        | N          | current status of drone         |
| [MSP_MOTOR](msp104.md)  | 104        | N          | sets motor from controller      |
| MSP_SET_MOTOR_HBRIDGE   | 215        | Y          | used to set Hbridge             |
