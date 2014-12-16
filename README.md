# Quarks - Interoperable Sensor Identifiers

A `quark` is a unique identifier to a single input and/or output on a hardware device, designed to be easy to manage for debugging/development and also wire/memory efficient.

The `quark` is composed of a minimum 20 bit _local selector_ and a 10 bit _network selector_. The maximum size fits safely within a `uint32_t` leaving 2 additional bits for custom app-specific flags (such as enabled/disabled).  A `quark` is always displayed as [base32 encoded](http://tools.ietf.org/html/rfc3548) string of 6 characters (5 bits per character, lower case, no padding), using the alphabet `abcdefghijklmnopqrstuvwxyz234567`.

## Local Selector

* 10 - `id`, 5 - `type`, 5 - `capabilities`
* `id` - unique 2-character id that maps to a local pin, port, or software value, see the [map](map.md)
* `type` - the only type(s) of data supported by the quark, a subset of JSON
  * `f` - flag (true/false)
  * `n` - number (JSON)
  * `s` - string (UTF8)
  * `b` - raw bytes (array of [0,1,0,0,...])
  * `m` - supports multiple types
* `capabilities` - what are the limitations when interacting with this quark
  * `r` - readable, can only return data (no write support)
  * `w` - writeable, can only be sent data (no read support)
  * `x` - may support either read and/or write (doesn't guarantee either)
  * `d` - dynamic, can generate a stream of events as it changes

## Network Selector

The last two characters (10 bits) are for identifying a quark in a local network, so that a single quark id can be used to address different devices on the network.  It requires the devices to use a network coordinator or be managed such that they have a unique local id and mappings for how to send requests to other devices when processing quarks with a network selector.

The special value `77` (ten high/1 bits) is reserved to always mean "localhost" or the current device whenever it is used.

## Examples

* `pofrab` - power status read-only flag on device 1
* `idsr77` - local device id string
* `tcndaa` current temperature value in celsius of device 0
* `dafx77` - true/false of local digital pin `D0`
* `acmdac` - number or string of analog pin `A4` on device 2
