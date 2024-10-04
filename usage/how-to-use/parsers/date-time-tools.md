---
description: Manage your date and time
icon: hourglass-clock
---

# Date/Time Tools

The `VcardCommonTools` class contains date and time parsers that allow you to parse an ISO-8601:2004 date and time format from a string to a `DateTimeOffset` that provides information about the parsed date and time. It also contains tools that allow you to save date and time back to an ISO-8601:2004 formatted string.

The following functions are available:

* `ParsePosixDate()`: Parses a date representation
* `TryParsePosixDate()`: Parses a date representation (boolean/out version)
* `ParsePosixTime()`: Parses a time representation
* `TryParsePosixTime()`: Parses a time representation (boolean/out version)
* `ParsePosixDateTime()`: Parses a date/time representation
* `TryParsePosixDateTime()`: Parses a date/time representation (boolean/out version)
* `ParsePosixTimestamp()`: Parses a timestamp representation
* `TryParsePosixTimestamp()`: Parses a timestamp representation (boolean/out version)
* `SavePosixDate()`: Saves to a date representation

For UTC offsets, you can parse a UTC offset from a string that is formatted with a basic or an extended ISO-8601 UTC offset prefixed with either a plus or a minus sign to a `TimeSpan` instance. You can also save them back to the formatted string.

The following functions are available:

* `ParseUtcOffset()`
* `SaveUtcOffset()`
