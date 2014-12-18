## Quark ID Map

Every quark has a unique ID that is 2 characters of `abcdefghijklmnopqrstuvwxyz234567` (base32), this is the authorative map of those values.

Since a quark is intended to be easier for a person to interpret, these mappings attempt to use character values that are recognizable.

All values not in the table are `reserved` for future use.  Custom ranges are set aside in the table that are available for any application or hardware specific ids.  The values in the range `2a` through `77` are permanently disabled to ensure that a quark always starts with an alpha character.

| first | last | value |
|:-----:|:----:|:-----:|
| aa    | a7   | analog/voltage pins A0, A1, ... A31
| ca    | c7   | OPEN - custom usage (firmware)
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
| ja    | j7   | OPEN - custom usage (configuration)
| la    | lp   | LEDs 1 through 16
| na    |      | name (product name, string)
| nd    |      | name - distributor
| nm    |      | name - manufacturer
| pb    |      | power - battery
| pc    |      | power - charging
| po    |      | power status (on/off)
| qa    | q7   | OPEN - custom usage (programmed scripts)
| ra    | rh   | rotational speed, fans, steppers
| sa    | sh   | "slot" information (up to 8), for attached devices
| si    | sp   | serial interfaces, si = default serial console (Serial0)
| ta    | th   | temperature
| up    |      | uptime
| vf    |      | version - firmware/bios (build)
| vp    |      | version - part number
| vn    |      | version - serial number
| xa    | x7   | OPEN - custom usage (hardware)
| 2a    | 77   | disabled
