# GPS Notes

- uses GLL over UART (serial) to provide DD format data using NMEA 0183 sentence formats

This can be read as:

```$<TalkerID>GLL,<Lat>,<N/S>,<Long>,<E/W>,<Timestamp>,<Status>,<ModeInd>*<checksum><CR><LF>3```

**$** - Starts the sentence
**TalkerID** - Two-letter identifier for the type of GPS system (e.g., GP for GPS)
**GLL** - Indicates it's a Geographic Latitude/Longitude message
**Lat** - Latitude in the format DDMM.MMMMM (degrees and decimal minutes)
**N/S** - North or South indicator
**Long** - Longitude in the format DDDMM.MMMMM (degrees and decimal minutes)
**E/W** - East or West indicator
**Timestamp** - UTC time in HHMMSS.SS format
**Status** - A for valid, V for invalid
**ModeInd** - Mode indicator (e.g., A for Autonomous, D for Differential)
**Separator** for the checksum
**Checksum** - Two-character hexadecimal value
**<CR><LF>** - Carriage return and line feed, ending the sentence23
An example of a GLL sentence looks like this:
```$GPGLL,3953.88008971,N,10506.75318910,W,034138.00,A,D*7```
