---
description: Manage your date and time
icon: hourglass-clock
---

# Date/Time Tools

The `VcardCommonTools` class contains date and time parsers that allow you to parse an ISO-8601:2004 date and time format from a string to a `DateTimeOffset` that provides information about the parsed date and time. It also contains tools that allow you to save date and time back to an ISO-8601:2004 formatted string.

<details>

<summary>Functions for parsing dates and times</summary>

The following functions are available:

<table><thead><tr><th width="415.6666259765625">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>ParsePosixDate()/TryParsePosixDate()</code></td><td>Parses a date string</td></tr><tr><td><code>ParsePosixTime()/TryParsePosixTime()</code></td><td>Parses a time string</td></tr><tr><td><code>ParsePosixDateTime()/TryParsePosixDateTime()</code></td><td>Parses a date/time string</td></tr><tr><td><code>ParsePosixTimestamp()/TryParsePosixTimestamp()</code></td><td>Parses a timestamp string</td></tr><tr><td><code>SavePosixDate()</code></td><td>Saves to a date representation</td></tr></tbody></table>

{% hint style="info" %}
Functions that are prefixed with `Try` return a boolean value indicating success, with the output as an `out` argument.
{% endhint %}

</details>

***

## <mark style="color:$primary;">UTC offsets</mark>

For UTC offsets, you can parse a UTC offset from a string that is formatted with a basic or an extended ISO-8601 UTC offset prefixed with either a plus or a minus sign to a `TimeSpan` instance. You can also save them back to the formatted string.

<details>

<summary>Functions for parsing UTC offsets</summary>

The following functions are available:

<table><thead><tr><th width="179.6666259765625">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>ParseUtcOffset()</code></td><td>Parses a UTC offset string</td></tr><tr><td><code>SaveUtcOffset()</code></td><td>Saves to a UTC offset string</td></tr></tbody></table>

</details>
