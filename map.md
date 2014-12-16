## Quark ID Map

Every quark has a unique ID that is 2 characters of `abcdefghijklmnopqrstuvwxyz234567` (base32), this is the authorative map of those values.

Since a quark is intended to be easier for a person to interpret, these mappings attempt to use character values that are recognizable.

All values not in the table are `reserved`.  There are 191 custom values available in the range `2a` through `76` for any needs outside of this map or for dynamic IDs.

| first | last | value |
|:-----:|:----:|:-----:|
| aa    | a7   | analog pins A0, A1, ... A31
| da    | d7   | digital pins D0, D1, ... D31
| ga    |      | gps - altitude
| gl    |      | gps - long (lambda)
| gp    |      | gps - lat (phi)
| gs    |      | gps (lat,lng)
| id    |      | device id (network)
| la    | lp   | LEDs 1 through 16
| pb    |      | power - battery
| pc    |      | power - charging
| po    |      | power status (on/off)
| sn    |      | serial number
| tc    |      | temperature (celsius)
| tf    |      | temperature (fahrenheit)
| ue    |      | uptime (epoch)
| um    |      | uptime (milliseconds)
| us    |      | uptime (seconds)
| vn    |      | version number (firmware build)
| 2a    | 76   | custom mappings (any use)
| 77    |      | reserved
