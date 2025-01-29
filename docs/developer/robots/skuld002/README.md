# SKU LD002


# Bill Of Materials

## Raspberry Pi 4B

[Datasheet](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-datasheet.pdf)

## SEN0304 x 3
[Datasheet](https://www.mouser.com/pdfDocs/ProductOverview_DFRobot_SEN0304.pdf)

- range  150cm, 300cm, 500cm (selectable)
- voltage 3.3v or 5.5 DC
- resolution 1cm (increments)
- 20mA operating current

## U-blox NEO-6M Compatible GPS Module

[datasheet](https://content.u-blox.com/sites/default/files/products/documents/NEO-6_DataSheet_%28GPS.G6-HW-09005%29.pdf)

- voltage 3.3v
- current 10mA

[see GPS](gps.md)


# Circuit Board Notes

For current calculation, the formula is $R = \frac{V}{I_m}$

where:
- R = resistance measured in Ohms
- V = voltage measured in volts
- I = current measured in Amps

For ultra-sonics the calculation becomes:

$R = \frac{V}{3I_m}$

the coefficients being the 3 SEN0304.

$R = \frac{3.3}{3(20 \times 0.001)} = \frac{3.3}{3(20 \times 0.001)} = \frac{3.3}{0.06} = 55\Omega$ 

therefore the capacitor required is:

$V(t) = V_0.e^-\frac{t}{RC}$

Where:
- V(t) = Voltage at time  3.3v
- V₀ = Initial voltage 3.3v
- R = Resistance (55$\Omega$)
- C = Capacitance
- t = Time (10ms = 0.01s)

# References

[Arduino 33 BLE Pins](https://axodyne.com/2020/06/arduino-33-ble-pins/)