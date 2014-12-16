# Quarks - Interoperable Sensor Identifiers

A `quark` is a unique identifier to a single input and/or output on a hardware device, designed to be easy to manage for debugging/development and also wire/memory efficient.

The `quark` is composed of a minimum 20 bit _local selector_ with an optional additional 10 bit _network selector_. The maximum size fits safely within a `uint32_t` leaving 2 additional bits for custom app-specific flags (such as enabled/disabled).  A `quark` is always displayed as [base32 encoded](http://tools.ietf.org/html/rfc3548) string of either 4 or 6 characters (no padding).

## Local Selector

* 5 - `type`, 5 - `capabilities`, 10 - `id`
* `type` - the type of data, a subset of JSON
  * `f`lag (true/false)
  * `n`umber (JSON)
  * `s`tring (UTF8)
  * `b`ytes (array of 0, 1, 0, 0, etc)
  * `a`ny (all types supported)
* `capabilities` - what is possible when interacting with this quark
  * `r`eadable - can only return data
  * `w`riteable - can only be sent data
  * `b`idirectional - read or write
  * `e`venting - generates events as it changes
* `id` - unique 2-character id that maps to a local pin, port, or software value
  * analog - `a?`
  * digital - `d?`
  * led - `la` to `lp`
  * custom - `2?` through `7?`
  * all other values are to be defined here in a table, such as temperature, LEDs, power, uptime, GPS, etc.

## Network Selector

The last two optional characters or 10 bits are for when a quark is used in a local network, so that a single quark id can be used to address different devices on the local network.  It requires the devices to use a network coordinator or be managed such that they have a unique local id and mappings for how to send requests to other devices when processing quarks with a network selector.

The special value `aa` (ten zero bits) is reserved to always mean "localhost" or the current device, it is the default if a 4-character quark is processed in a network context.
