# MSP 8

When in flight path mode, a series of waypoints are sent using an array of waypoints.


# Waypoints

### longitude

For robots fitted with GPS, these are angular distances of expected state change west or east, of 
Greenwich meridian.

For robot without GPS, indicates distance west or east of the drones current position measured
in centimeters where positive integers indicate west state changes, and negative integers represent
eastward changes of drones current position.

### latitude

For robots fitted with GPS, these are angular distances of expected state change north or south, of
Greenwich meridian. Using Decimal Degrees 

For robot without GPS, indicates distance south or north of the drones current position measured
in centimeters where positive integers indicate west state changes, and negative integers represent
eastward changes of drones current position.

### altitude

Only available for drones with GPS,  indicates the expected altitude change of drone. Measured in
centimeters.

### time_delta

Coefficient of multiples of thread_wait_time, measured from drones current state.

## Command Construction

# Client Request

```
{
   "command": "MSP_WAYPONTS",
   "payload: {
        "waypoints": [
            {
                "longatude": "-38.226214845564414",
                "latitide": "144.3762847823173",
                "altitude": 30000,
                "time_delta": 1
            },
            {
                "longatude": "-38.226214845564414",
                "latitide": "144.3762847823173",
                "altitude": 516400,
                "time_delta": 5
            },
            {
                "longatude": "-38.235907",
                "latitide": "144.371845",
                "altitude": 516400,
                "time_delta": 460     
            },
                        {
                "longatude": "-38.235907",
                "latitide": "144.371845",
                "altitude": 0,
                "time_delta": 1     
            }
        ]
   }
}
```
