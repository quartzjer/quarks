# Quarks - Interoperable Device Identifiers

A `quark` is a unique identifier to a single input and/or output on a hardware device, designed to be easy to manage for debugging/development and also wire/memory efficient.

The `quark` is composed of a minimum 20 bit _local selector_ and a 10 bit _network selector_. The maximum size fits safely within a `uint32_t` leaving 2 additional bits for custom app-specific flags (such as enabled/disabled).  A `quark` is always displayed as [base32 encoded](http://tools.ietf.org/html/rfc3548) string of 6 characters (5 bits per character, lower case, no padding), using the alphabet `abcdefghijklmnopqrstuvwxyz234567`.

## Local Selector

* 10 - `id`, 5 - `capabilities`, 5 - `data type`
* `id` - unique 2-character id that maps to a local pin, port, or software value, see the [map](map.md)
* `capabilities` - what are the limitations when interacting with this quark
  * `r` - readable, can only return data (no write support)
  * `w` - readable and writeable (doesn't guarantee readability)
  * `x` - can generate a stream of events as it changes
* `data type` - the only type(s) of data supported by the quark, a subset of JSON
  * `f` - flag (true/false)
  * `n` - number (JSON)
  * `s` - string (UTF8)
  * `b` - raw bytes (array of [0,1,0,0,...])
  * `m` - supports multiple types

### `capabilities`

The capabilities field is only used to identify what the hardware is able to do, not serve as a method for limiting access, it is an identifier not an ACL/mask.  A quark with `r` identical to one with `w` or `x` should never exist, each capability is a superset of the previous.

The `x` eventing capability is a signal to the application that it is able to generate events containing the identical `r` data, but how the events are delivered depends on the network technology available and in use, as well as how the subscriptions are managed.

### `data type`

Each quark may support just one data type or the `m` if it handles any multiple of them, `m` is a superset and like capabilities there should never be an identical quark with only differing data types.

The `m` type should be used to return different types for different use cases, such as a hardware fault should return the flag if there is one, the number is a code, the string is an error message, and the bytes may be extra detail.  They must always be derived from the same data but should take advantage of the actual data type to provide a richer result.

## Network Selector

The last two characters (10 bits) are for identifying a quark in a local network, so that a single quark id can be used to address different devices on the network.  It requires the devices to use a network coordinator or be managed such that they have a unique local id and mappings for how to send requests to other devices when processing quarks with a network selector.

Device `0` would be `aa`, device `1` would be `ab`, etc. The special value `77` (ten high/1 bits) is reserved to always mean "localhost" or the current device whenever it is used.

## Examples

* `porfab` - power status read-only flag on device 1
* `idrs77` - local device id string
* `tcxnaa` current temperature value in celsius of device 0
* `dawf77` - true/false of local digital pin `D0`
* `acxmac` - full support for anything to analog pin `A3` on device 2
