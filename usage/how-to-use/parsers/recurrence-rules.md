---
description: Repeat, repeat, repeat
icon: arrow-rotate-right
---

# Recurrence Rules

Recurrence rules are event, to-do, journal, or standard and daylight timezone repetition instances that define how to repeat a specific number of times using a rule that adjusts the number of days, weeks, or a time unit in which the repetition occurs. These rules adjust how to repeat an event.

{% hint style="info" %}
This is only applicable to calendars, but you can use the parser anywhere.
{% endhint %}

The recurrence rule parser has two versions:

* Version 1, which uses The Open Group's Calendaring and Scheduling API (XCS)'s extended recurrence rule grammar (also found in [vCalendar 1.0's specification](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-10.txt#L1176)) and returns more than one rule
* Version 2, which uses vCalendar 2.0's [recurrence rule grammar](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt#L2106) and returns a single rule

You can see how to construct your own recurrence rule using the above links. The recurrence rules can be parsed using one of the following functions found in the `RecurrenceParser` class:

* Version 1: `ParseRuleV1()`
* Version 2: `ParseRuleV2()`

{% hint style="info" %}
These functions are named after the method that the appropriate vCalendar versions uses.
{% endhint %}

After parsing, these functions return an array of recurrence rules (version 1) or a recurrence rule instance (version 2) using the `RecurrenceRule` class. It contains a few properties that are categorized into the following:

* General
  * `Version`: Recurrence rule version.
  * `Frequency`: Recurrence frequency that describes the granularity of the repetition.
  * `Internal`: Repeat frequency.
  * `Duration`: Number of occurrences that this rule generates.
  * `EndDate`: Specifies whether this date is the last time to repeat.
* vCalendar 1.0
  * `V1TimePeriods`: Time periods for daily frequency. `isEnd` indicates the end marker.
  * `V1DayTimes`: Days of week for weekly frequency. `isEnd` indicates the end marker
  * `V1MonthlyOccurrences`: Monthly occurrences. `isEnd` indicates the end marker.
  * `V1MonthlyDayNumbers`: Monthly by day numbers. `isEnd` indicates the end marker.
  * `V1YearlyMonthNumbers`: Yearly by month numbers. `isEnd` indicates the end marker.
  * `V1YearlyDayNumbers`: Yearly by day numbers. `isEnd` indicates the end marker.
* vCalendar 2.0
  * `StartWeekday`: A day that defines the start of the week.
  * `V2Seconds`: List of seconds.
  * `V2Minutes`: List of minutes.
  * `V2Hours`: List of hours.
  * `V2Days`: List of days
  * `V2MonthlyDays`: List of days of month.
  * `V2YearlyDays`: List of days of year.
  * `V2WeekNumbers`: List of week numbers.
  * `V2MonthNumbers`: List of month numbers.
  * `V2Positions`: List of positions.
