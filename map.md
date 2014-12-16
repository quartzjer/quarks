## Quark ID Map

Every quark has a unique ID that is 2 characters of `abcdefghijklmnopqrstuvwxyz234567` (base32), this is the authorative map of those values.

Since a quark is intended to be easier for a person to interpret, these mappings attempt to use character values that are recognizable.

All values not in the table are `reserved`.  There are 191 custom values available in the range `2a` through `76` for any needs outside of this map or for dynamic IDs.

| first | last | value |
|:-----:|:----:|:-----:|
| aa    | a7   | analog/voltage pins A0, A1, ... A31
| da    | d7   | digital pins D0, D1, ... D31
| fd    |      | free disk
| fe    |      | free eeprom
| fr    |      | free ram
| ga    |      | gps - altitude
| gl    |      | gps - long (lambda)
| gp    |      | gps - lat (phi)
| gs    |      | gps (lat,lng)
| hb    |      | hardware boot device/mode
| hc    |      | hardware clock, datetime
| hn    |      | device hashname
| hs    |      | hardware speed, cpu
| hf    |      | last hardware fault
| id    |      | device id (quark network selector)
| ik    |      | device key
| ip    |      | IP address
| is    |      | network interface status/speed, signal strength
| la    | lp   | LEDs 1 through 16
| na    |      | name (product name, string)
| nd    |      | name - distributor
| nm    |      | name - manufacturer
| pb    |      | power - battery
| pc    |      | power - charging
| po    |      | power status (on/off)
| ra    | rh   | rotational speed, fans, steppers
| sa    | sh   | "slot" information (up to 8), for attached devices
| si    | sp   | serial interfaces, si = default serial console (Serial0)
| ta    | th   | temperature
| up    |      | uptime
| vf    |      | version - firmware/bios (build)
| vp    |      | version - part number
| vn    |      | version - serial number
| 2a    | 76   | custom mappings (any use)
| 77    |      | reserved
