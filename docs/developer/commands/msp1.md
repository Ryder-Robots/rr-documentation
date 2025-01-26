# MSP 1


Sent from Client software to change mode of the drone. 

## Members 

### Mode

Current modes are:

#### CMODE_NOT_SET

Initial mode that indicates that client has not set a mode. 

Bitmask: 0b000100000000

#### CMODE_MANUAL_FLIGHT

Manual mode to capture data for training. When this mode is set, expected requests will be
(MSP104 Requests)[msp104.md]

Bitmask: 0b001000000000

#### CMODE_PATH_PLANNER

When CMODE_PATH_PLANNER is selected, client is expected to send (MSP 8 requests)[msp8.md]

Bitmask: 0b010000000000

## Client Request Format

```
{
    "command": "MSP_MODE",
    "payload": {
        "mode": "CMODE_PATH_PLANNER"
    }
}
```
