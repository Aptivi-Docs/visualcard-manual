---
description: What's the duration or the period of the event?
icon: watch
---

# Durations and Periods

VisualCard offers a duration parser that allows you to parse a string representation of the duration as specified in the ISO-8601:2004 format. A single function that you can use is `GetDurationSpan()` from the `vCardCommonTools` class.

Once parsing is done, if the syntax is valid, it returns a tuple of both the `DateTimeOffset` that describes a resulting end date added to either a current date or a specified root date, and a `TimeSpan` that describes the processed duration.

{% hint style="info" %}
For vCalendar 2.0, month and year specifiers are not supported, but vCalendar 1.0 does. You can review the duration specifier [here](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt#L1929).
{% endhint %}

Periods describe a start date and an end date for a specific time ranged events, and can be described as a precise period of time. You can see its specification from the vCard 2.0 spec [here](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt#L2050). `GetTimePeriod()` allows you to parse a period string and convert it to an appropriate `TimePeriod` class that has the following properties:

* `StartDate`: A `DateTimeOffset` instance that contains an event start date
* `EndDate`: A `DateTimeOffset` instance that contains an event end date
* `Duration`: A `TimeSpan` instance that contains a computed duration of a time period
