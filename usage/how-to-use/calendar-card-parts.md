---
description: How do the calendar parts work in VisualCard?
icon: calendar
---

# Calendar Parts

Normally, calendars in VisualCard have three types of parts that define a calendar:

* Strings (`GetString()`)
* Integers (`GetInteger()`)
* Array of parts (`GetPartsArray()`)

In the current version of VisualCard, the following parts are supported:

<table><thead><tr><th width="267">Key</th><th width="169">Type</th><th width="187">Component</th><th width="59">1.0</th><th width="65">2.0</th></tr></thead><tbody><tr><td><code>PRODID</code></td><td>String</td><td>Root</td><td>●</td><td>●</td></tr><tr><td><code>METHOD</code></td><td>String</td><td>Root</td><td></td><td>●</td></tr><tr><td><code>CALSCALE</code></td><td>String</td><td>Root</td><td></td><td>●</td></tr><tr><td><code>ATTACH</code></td><td>Array</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>CATEGORIES</code></td><td>Array</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>COMMENT</code></td><td>Array</td><td>Event, to-do, journal, or free/busy</td><td></td><td>●</td></tr><tr><td><code>GEO</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td>●</td></tr><tr><td><code>LOCATION</code></td><td>Array</td><td>Event or to-do</td><td></td><td>●</td></tr><tr><td><code>RESOURCES</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td>●</td></tr><tr><td><code>ATTENDEE</code></td><td>Array</td><td>Event, to-do, journal, free/busy, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>CREATED</code></td><td>Array</td><td>Event, to-do, or journal</td><td></td><td>●</td></tr><tr><td><code>DCREATED</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>DTSTART</code></td><td>Array</td><td>Event, to-do, free/busy, or standard/daylight timezone components</td><td>●</td><td>●</td></tr><tr><td><code>DTEND</code></td><td>Array</td><td>Event or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>DTSTAMP</code></td><td>Array</td><td>Event</td><td></td><td>●</td></tr><tr><td><code>CLASS</code></td><td>String</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>UID</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>ORGANIZER</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>STATUS</code></td><td>String</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>SUMMARY</code></td><td>String</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>DESCRIPTION</code></td><td>String</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>TRANSP</code></td><td>String</td><td>Event</td><td>●</td><td>●</td></tr><tr><td><code>ACTION</code></td><td>String</td><td>Alarm</td><td></td><td>●</td></tr><tr><td><code>TRIGGER</code></td><td>String</td><td>Alarm</td><td></td><td>●</td></tr><tr><td><code>TZID</code></td><td>String</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZURL</code></td><td>String</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZNAME</code></td><td>Array</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZOFFSETFROM</code></td><td>Integer</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZOFFSETTO</code></td><td>Integer</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>RRULE</code></td><td>String</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>RDATE</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>EXDATE</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>PRIORITY</code></td><td>Integer</td><td>Event or to-do</td><td></td><td>●</td></tr><tr><td><code>SEQUENCE</code></td><td>Integer</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>PERCENT-COMPLETION</code></td><td>Integer</td><td>To-do</td><td></td><td>●</td></tr><tr><td><code>COMPLETED</code></td><td>Array</td><td>To-do</td><td>●</td><td>●</td></tr><tr><td><code>DUE</code></td><td>Array</td><td>To-do</td><td>●</td><td>●</td></tr><tr><td><code>DAYLIGHT</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td></td></tr><tr><td><code>AALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>DALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>MALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>PALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>RELATED-TO</code></td><td>Array</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr></tbody></table>

The following status types that are allowed in events, to-dos, or journals are:

* vCalendar 1.0
  * Event
    * `NEEDS ACTION`
    * `SENT`
    * `TENTATIVE`
    * `CONFIRMED`
    * `DECLINED`
    * `DELEGATED`
  * To-do
    * `NEEDS ACTION`
    * `SENT`
    * `ACCEPTED`
    * `COMPLETED`
    * `DECLINED`
    * `DELEGATED`
* vCalendar 2.0
  * Event
    * `TENTATIVE`
    * `CONFIRMED`
    * `CANCELLED`
  * To-do
    * `NEEDS-ACTION`
    * `COMPLETED`
    * `IN-PROCESS`
    * `CANCELLED`
  * Journal
    * `DRAFT`
    * `FINAL`
    * `CANCELLED`

Additionally, the event or to-do alarm type for a single alarm component can be one of:

* `AUDIO`
* `DISPLAY`
* `EMAIL`

For the `ATTENDEE` property, you can either specify nothing as a type (without typing the `TYPE=` parameter) or specify VCARD and any X-nonstandard type. Same applies for the `AALARM` property, except that it supports only `PCM`, `WAVE`, `AIFF`, and any X-nonstandard type as types.

The below sections describe how exactly to parse all the supported types.

## Strings

Strings in vCalendar and VisualCard are the simplest of the types that allow you to input just text that represent that property. The above table shows all the properties, and those that are listed as a String, such as `CLASS`, can be get as a string using a function called `GetString()`.

This function returns one of the following strings:

* **An empty string**
  * If the string is not supported in the calendar's vCalendar version.
  * If the string is not defined in the calendar's vCalendar instance.
  * If the string is explicitly blank.
* **A string value**
  * If the string is defined, supported, and is not empty.

## Integers

Integers in vCalendar and VisualCard are the simplest of the types that allow you to input just a number that represents that property. The above table shows all the properties, and those that are listed as an Integer, such as `PRIORITY`, can be get as an integer using a function called `GetInteger()`.

This function returns one of the following integers:

* **-1**
  * If the integer is not supported in the contact's vCard version.
  * If the integer is not defined in the contact's vCard instance.
  * If the integer is specified as -1
* **An integer value**
  * If the integer is defined and supported.

## Array of Parts

Parts that can be more than one part (i.e. can be put to an array and can exist more than once per vCard instance) exist in vCard. The above table shows all the properties that are listed as an Array. If they are listed as such, like `ATTENDEE`, you can get it using `GetPartsArray()`.

`GetPartsArray()` is a generic method. This means that you can specify one of the `Info` classes, as long as it represents a valid class that points to a valid part, such as `AttendeeInfo`. In this case, you'll have to call it like this:

```csharp
// Either
Calendar.Events[0].GetPartsArray<AttendeeInfo>()

// or
Calendar.Events[0].GetPartsArray<AttendeeInfo>(CalendarPartsArrayEnum.Attendee)
```

You can directly get a value of a property without having to cast the resultant part to the correct part info class. The same base properties also apply to the normal Parts.

{% hint style="info" %}
You can also get any parts array as a base, though you can't call the non-parameterized function against the base part, `BaseCardPartInfo`. You'll also have to cast the resultant part if you need to access something other than the base properties as mentioned above.

```csharp
Calendar.Events[0].GetPartsArray<BaseCardPartInfo>(CalendarPartsArrayEnum.Attendee)
```
{% endhint %}

This function returns one of the following:

* **An empty array**
  * If the parts array is not supported in the contact's vCard version
  * If the parts array is not defined in the contact's vCard instance
* **An array of parts**
  * If the part is supported and defined in the contact's vCard instance

{% hint style="danger" %}
Any attempt to specify an incorrect type or enumeration in the second overload of `GetPartsArray`, such as `Calendar.Events[0].GetPartsArray<DateCreatedInfo>(CalendarPartsArrayEnum.Attendee)`, will throw an exception. However, it doesn't throw an exception in case `BaseCardPartInfo` is specified.
{% endhint %}

## Getting a Blob Stream

Image parts, icon parts, sound parts, and key parts in a vCalendar instance allow you to get a blob stream from the encoded data that allows you to represent the actual data decoded from the BASE64 encoding as a blob. VisualCard exposes this feature to allow you to perform various operations on them, such as displaying calendar attachments, saving sound attachments as sound files, etc.

You can make use of this feature by invoking the `GetBlobData()` function from the `VcardParserTools` class.

{% hint style="danger" %}
This feature doesn't support non-blob values, such as an HTTPS URL to a logo file.
{% endhint %}

## Events, To-dos, and more

A calendar instance may contain one or more of the following components nested inside the root calendar component:

* Events
* To-dos
* Journals
* Free/busy instances
* Timezones
  * Standard times
  * Daylight times
* Event and to-do alarms

You can access this information using their individual properties found in the calendar instance as follows:

* `Events`
  * `Alarms`
* `Todos`
  * `Alarms`
* `Journals`
* `FreeBusyList`
* `TimeZones`
  * `StandardTimeList`
  * `DaylightTimeList`
