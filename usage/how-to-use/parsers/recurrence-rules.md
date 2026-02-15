---
description: Repeat, repeat, repeat
icon: arrow-rotate-right
---

# Recurrence Rules

Recurrence rules are event, to-do, journal, or standard and daylight timezone repetition instances that define how to repeat a specific number of times using a rule that adjusts the number of days, weeks, or a time unit in which the repetition occurs. These rules adjust how to repeat an event.

{% hint style="info" %}
This is only applicable to calendars, but you can use the parser anywhere.
{% endhint %}

***

## <mark style="color:$primary;">Versions of the recurrence rule parser</mark>

The recurrence rule parser has two versions:

* Version 1, which uses The Open Group's Calendaring and Scheduling API (XCS)'s extended recurrence rule grammar (also found in [vCalendar 1.0's specification](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-10.txt#L1176)) and returns more than one rule
* Version 2, which uses vCalendar 2.0's [recurrence rule grammar](https://github.com/Aptivi/VisualCard/blob/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt#L2106) and returns a single rule

You can see how to construct your own recurrence rule using the above links. The recurrence rules can be parsed using one of the following functions found in the `RecurrenceParser` class:

* Version 1: `ParseRuleV1()`
* Version 2: `ParseRuleV2()`

{% hint style="info" %}
These functions are named after the method that the appropriate vCalendar versions uses.
{% endhint %}

***

## <mark style="color:$primary;">Recurrence rule properties</mark>

After parsing, these functions return an array of recurrence rules (version 1) or a recurrence rule instance (version 2) using the `RecurrenceRule` class.

<details>

<summary>General properties</summary>

All properties about a recurrence rule that are applied globally are:

<table><thead><tr><th width="129.66668701171875">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Version</code></td><td>Recurrence rule version</td></tr><tr><td><code>Frequency</code></td><td>Recurrence frequency that describes the granularity of the repetition</td></tr><tr><td><code>Internal</code></td><td>Repeat frequency</td></tr><tr><td><code>Duration</code></td><td>Number of occurrences that this rule generates</td></tr><tr><td><code>EndDate</code></td><td>Specifies whether this date is the last time to repeat</td></tr></tbody></table>

</details>

<details>

<summary>vCalendar 1.0 recurrence rule properties</summary>

The below properties only apply to vCalendar 1.0:

<table><thead><tr><th width="200.3333740234375">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>V1TimePeriods</code></td><td>Time periods for daily frequency</td></tr><tr><td><code>V1DayTimes</code></td><td>Days of week for weekly frequency</td></tr><tr><td><code>V1MonthlyOccurrences</code></td><td>Monthly occurrences</td></tr><tr><td><code>V1MonthlyDayNumbers</code></td><td>Monthly by day numbers</td></tr><tr><td><code>V1YearlyMonthNumbers</code></td><td>Yearly by month numbers</td></tr><tr><td><code>V1YearlyDayNumbers</code></td><td>Yearly by day numbers</td></tr></tbody></table>

{% hint style="info" %}
For all properties mentioned above, `isEnd` indicates the end marker.
{% endhint %}

</details>

<details>

<summary>vCalendar 2.0 recurrence rule properties</summary>

The below properties only apply to vCalendar 2.0:

<table><thead><tr><th width="200.3333740234375">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>StartWeekday</code></td><td>A day that defines the start of the week</td></tr><tr><td><code>V2Seconds</code></td><td>List of seconds</td></tr><tr><td><code>V2Minutes</code></td><td>List of minutes</td></tr><tr><td><code>V2Hours</code></td><td>List of hours</td></tr><tr><td><code>V2Days</code></td><td>List of days</td></tr><tr><td><code>V2MonthlyDays</code></td><td>List of days of month</td></tr><tr><td><code>V2YearlyDays</code></td><td>List of days of year</td></tr><tr><td><code>V2WeekNumbers</code></td><td>List of week numbers</td></tr><tr><td><code>V2MonthNumbers</code></td><td>List of month numbers</td></tr><tr><td><code>V2Positions</code></td><td>List of positions</td></tr></tbody></table>

</details>
