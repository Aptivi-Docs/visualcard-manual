---
description: How do the calendar parts work in VisualCard?
icon: calendar
---

# Calendar Parts

Normally, calendars in VisualCard have three types of parts that define a calendar:

* Strings
* Integers
* Array of parts

<details>

<summary>Supported calendar parts across vCalendar versions</summary>

In the current version of VisualCard, the following parts are supported:

<table><thead><tr><th width="183.6666259765625">Key</th><th width="92.6666259765625">Type</th><th width="262.3333740234375">Component</th><th width="71.3333740234375">1.0</th><th width="71.3333740234375">2.0</th></tr></thead><tbody><tr><td><code>PRODID</code></td><td>String</td><td>Root</td><td>●</td><td>●</td></tr><tr><td><code>METHOD</code></td><td>String</td><td>Root</td><td></td><td>●</td></tr><tr><td><code>CALSCALE</code></td><td>String</td><td>Root</td><td></td><td>●</td></tr><tr><td><code>ATTACH</code></td><td>Array</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>CATEGORIES</code></td><td>Array</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>COMMENT</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td></td><td>●</td></tr><tr><td><code>GEO</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td>●</td></tr><tr><td><code>LOCATION</code></td><td>String</td><td>Event or to-do</td><td></td><td>●</td></tr><tr><td><code>RESOURCES</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td>●</td></tr><tr><td><code>ATTENDEE</code></td><td>String</td><td>Event, to-do, journal, free/busy, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>CREATED</code></td><td>Array</td><td>Event, to-do, or journal</td><td></td><td>●</td></tr><tr><td><code>DCREATED</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>DTSTART</code></td><td>Array</td><td>Event, to-do, free/busy, or standard/daylight timezone components</td><td>●</td><td>●</td></tr><tr><td><code>DTEND</code></td><td>Array</td><td>Event or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>DTSTAMP</code></td><td>Array</td><td>Event</td><td></td><td>●</td></tr><tr><td><code>CLASS</code></td><td>String</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>UID</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>ORGANIZER</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>STATUS</code></td><td>String</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>SUMMARY</code></td><td>String</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>DESCRIPTION</code></td><td>String</td><td>Event, to-do, journal, or alarm</td><td>●</td><td>●</td></tr><tr><td><code>TRANSP</code></td><td>String</td><td>Event</td><td>●</td><td>●</td></tr><tr><td><code>ACTION</code></td><td>String</td><td>Alarm</td><td></td><td>●</td></tr><tr><td><code>TRIGGER</code></td><td>String</td><td>Alarm</td><td></td><td>●</td></tr><tr><td><code>TZID</code></td><td>String</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZURL</code></td><td>String</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZNAME</code></td><td>String</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZOFFSETFROM</code></td><td>Integer</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>TZOFFSETTO</code></td><td>Integer</td><td>Timezone</td><td></td><td>●</td></tr><tr><td><code>RRULE</code></td><td>String</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>RDATE</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>EXDATE</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td>●</td></tr><tr><td><code>PRIORITY</code></td><td>Integer</td><td>Event or to-do</td><td></td><td>●</td></tr><tr><td><code>SEQUENCE</code></td><td>Integer</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>PERCENT-COMPLETION</code></td><td>Integer</td><td>To-do</td><td></td><td>●</td></tr><tr><td><code>COMPLETED</code></td><td>Array</td><td>To-do</td><td>●</td><td>●</td></tr><tr><td><code>DUE</code></td><td>Array</td><td>To-do</td><td>●</td><td>●</td></tr><tr><td><code>DAYLIGHT</code></td><td>Array</td><td>Event, to-do, journal, or daylight and standard time zone components</td><td>●</td><td></td></tr><tr><td><code>AALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>DALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>MALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>PALARM</code></td><td>Array</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>RELATED-TO</code></td><td>String</td><td>Event, to-do, or journal</td><td>●</td><td>●</td></tr><tr><td><code>LAST-MODIFIED</code></td><td>Array</td><td>Event, to-do, journal, or time zone</td><td>●</td><td>●</td></tr><tr><td><code>EXRULE</code></td><td>String</td><td>Event or to-do</td><td>●</td><td></td></tr><tr><td><code>RECURRENCE-ID</code></td><td>String</td><td>Event, to-do, or journal</td><td></td><td>●</td></tr><tr><td><code>REPEAT</code></td><td>Integer</td><td>Alarm</td><td>●</td><td>●</td></tr><tr><td><code>DURATION</code></td><td>String</td><td>Event, to-do, or alarm</td><td></td><td>●</td></tr><tr><td><code>REQUEST-STATUS</code></td><td>Array</td><td>Event, to-do, journal, or free/busy</td><td></td><td>●</td></tr><tr><td><code>URL</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td>●</td><td>●</td></tr><tr><td><code>TZ</code></td><td>String</td><td>Root</td><td>●</td><td>●</td></tr><tr><td><code>CONTACT</code></td><td>String</td><td>Event, to-do, journal, or free/busy</td><td></td><td>●</td></tr><tr><td><code>RNUM</code></td><td>Integer</td><td>Event or to-do</td><td>●</td><td></td></tr></tbody></table>

</details>

<details>

<summary>Required calendar parts for vCalendar instances</summary>

When parsing vCalendar string representation, VisualCard checks for the below requirements:

* Root calendar component (after `START:VCALENDAR` before any `START:VCOMPONENT` specifier)
  * `PRODID` is required in vCalendar v2.0 but not v1.0
* Events and To-dos (after `START:VEVENT` or `START:VTODO`)
  * `UID` and `DTSTAMP` properties are required in vCalendar v2.0 but not v1.0

In addition to the above requirements, there are vCalendar 2.0 components that have their own requirements according to the specification:

* Journals and Free/Busy info (after `START:VJOURNAL` or `START:VFREEBUSY`)
  * `UID` and `DTSTAMP` properties are required
* Time zone info (after `START:VTIMEZONE` before standard/daylight components)
  * `TZID` is required
* Standard and daylight info (after `START:STANDARD` or `START:DAYLIGHT`)
  * `DTSTART` is required
  * `TZOFFSETFROM` and `TZOFFSETTO` is required

</details>

<details>

<summary>Creating an empty vCalendar instance</summary>

You can create empty calendar instances using the `Calendar` class constructor, but you'll have to specify a version of vCalendar to be used, such as 1.0 or 2.0. The simplest way to create a calendar instance with no properties is:

```csharp
var calendar = new Calendar(new(2, 0));
```

The same is true for calendar components, such as `CalendarAlarm` which you can use to add a new alarm to the calendar using `AddAlarm()` and remove an alarm from the calendar using `RemoveAlarm()`

</details>

***

## <mark style="color:$primary;">Types for some properties</mark>

For the `ATTENDEE` property, you can either specify nothing as a type (without typing the `TYPE=` parameter) or specify VCARD and any X-nonstandard type. Same applies for the `AALARM` property, except that it supports only `PCM`, `WAVE`, `AIFF`, and any X-nonstandard or IANA type as types.

{% hint style="info" %}
You can access all extra X-named and IANA properties by calling `GetExtraPartsArray`, passing it either the `XNameInfo` or the `ExtraInfo` type as a generic type argument. You can also get all parsed extra X-named and IANA calendar components using the `Others` property from the root calendar.
{% endhint %}

***

## <mark style="color:$primary;">Strings</mark>

Strings in vCalendar and VisualCard are the simplest of the types that allow you to input just text that represent that property.

<details>

<summary>Obtaining a string or a group of strings</summary>

String properties, such as `CLASS`, can be get as a string using a function called `GetString()`. You can also get a dictionary of a list of parsed strings using the `Strings` property.

This function returns one of the following strings:

* **An empty string**
  * If the string is not supported in the calendar's vCalendar version.
  * If the string is not defined in the calendar's vCalendar instance.
  * If the string is explicitly blank.
* **A string value**
  * If the string is defined, supported, and is not empty.

</details>

***

## <mark style="color:$primary;">Integers</mark>

Integers in vCalendar and VisualCard are the simplest of the types that allow you to input just a number that represents that property.

<details>

<summary>Obtaining an integer or a group of integers</summary>

Integer properties, such as `PRIORITY`, can be get as an integer using a function called `GetInteger()`. You can also get a dictionary of a list of parsed integers using the `Integers` property.

This function returns one of the following integers:

* **-1**
  * If the integer is not supported in the contact's vCard version.
  * If the integer is not defined in the contact's vCard instance.
  * If the integer is specified as -1
* **An integer value**
  * If the integer is defined and supported.

</details>

***

## <mark style="color:$primary;">Array of Parts</mark>

Parts that can be more than one part (i.e. can be put to an array and can exist more than once per vCalendar instance) exist in vCalendar.

<details>

<summary>Obtaining a parts array</summary>

Array properties like `ATTENDEE` can be get using `GetPartsArray()`. You can also get a dictionary of a list of parsed parts array lists using the `PartsArray` property.

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

</details>

***

## <mark style="color:$primary;">Miscellaneous operations</mark>

In addition to obtaining strings and parts array, you can also perform other operations that you can take a look at below:

<details>

<summary>Getting a Blob Stream</summary>

Image parts, icon parts, sound parts, and key parts in a vCalendar instance allow you to get a blob stream from the encoded data that allows you to represent the actual data decoded from the BASE64 encoding as a blob. VisualCard exposes this feature to allow you to perform various operations on them, such as displaying calendar attachments, saving sound attachments as sound files, etc.

You can make use of this feature by invoking the `GetBlobData()` function from the `VcardParserTools` class.

{% hint style="danger" %}
This feature doesn't support non-blob values, such as an HTTPS URL to a logo file.
{% endhint %}

</details>

<details>

<summary>Events, To-dos, and more</summary>

A calendar instance may contain one or more of the following components nested inside the root calendar component:

| Component           | Subcomponent   |
| ------------------- | -------------- |
| Events              | Event alarms   |
| To-dos              | To-do alarms   |
| Journals            |                |
| Free/busy instances |                |
| Timezones           | Standard times |
|                     | Daylight times |

### <mark style="color:$primary;">Accessing components</mark>

You can access this information using their individual properties found in the calendar instance as follows:

<table><thead><tr><th width="250.3333740234375">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Events</code></td><td>Gets a list of events</td></tr><tr><td><code>Events.Alarms</code></td><td>Gets a list of event alarms</td></tr><tr><td><code>Todos</code></td><td>Gets a list of todos</td></tr><tr><td><code>Todos.Alarms</code></td><td>Gets a list of todo alarms</td></tr><tr><td><code>Journals</code></td><td>Gets a list of journals</td></tr><tr><td><code>FreeBusyList</code></td><td>Gets a list of free-busy lists</td></tr><tr><td><code>TimeZones</code></td><td>Gets a list of time zones</td></tr><tr><td><code>TimeZones.StandardTimeList</code></td><td>Gets a list of time zone standard times</td></tr><tr><td><code>TimeZones.DaylightTimeList</code></td><td>Gets a list of time zone daylight times</td></tr></tbody></table>

### <mark style="color:$primary;">Adding and deleting components</mark>

You can add or remove compatible components to a calendar instance or its compatible parent component to add new information, such as adding new events or event alarms. The following functions are available:

<table><thead><tr><th width="250.3333740234375">Property</th><th>Functions</th></tr></thead><tbody><tr><td><code>Events</code></td><td><code>AddEvent()</code>, <code>DeleteEvent()</code></td></tr><tr><td><code>Events.Alarms</code></td><td><code>AddAlarm()</code>, <code>DeleteAlarm()</code></td></tr><tr><td><code>Todos</code></td><td><code>AddTodo()</code>, <code>DeleteTodo()</code></td></tr><tr><td><code>Todos.Alarms</code></td><td><code>AddAlarm()</code>, <code>DeleteAlarm()</code></td></tr><tr><td><code>Journals</code></td><td><code>AddJournal()</code>, <code>DeleteJournal()</code></td></tr><tr><td><code>FreeBusyList</code></td><td><code>AddFreeBusy()</code>, <code>DeleteFreeBusy()</code></td></tr><tr><td><code>TimeZones</code></td><td><code>AddTimeZone()</code>, <code>DeleteTimeZone()</code></td></tr><tr><td><code>TimeZones.StandardTimeList</code></td><td><code>AddStandardTime()</code>, <code>DeleteStandardTime()</code></td></tr><tr><td><code>TimeZones.DaylightTimeList</code></td><td><code>AddDaylightTime()</code>, <code>DeleteDaylightTime()</code></td></tr></tbody></table>

</details>

<details>

<summary>Supported status types</summary>

The following status types that are allowed in events, to-dos, or journals are:

| vCalendar version | Component | Status         |
| ----------------- | --------- | -------------- |
| v1.0              | Event     | `NEEDS ACTION` |
|                   |           | `SENT`         |
|                   |           | `TENTATIVE`    |
|                   |           | `CONFIRMED`    |
|                   |           | `DECLINED`     |
|                   |           | `DELEGATED`    |
|                   | To-do     | `NEEDS ACTION` |
|                   |           | `SENT`         |
|                   |           | `ACCEPTED`     |
|                   |           | `COMPLETED`    |
|                   |           | `DECLINED`     |
|                   |           | `DELEGATED`    |
| v2.0              | Event     | `TENTATIVE`    |
|                   |           | `CONFIRMED`    |
|                   |           | `CANCELLED`    |
|                   | To-do     | `NEEDS-ACTION` |
|                   |           | `COMPLETED`    |
|                   |           | `IN-PROCESS`   |
|                   |           | `CANCELLED`    |
|                   | Journal   | `DRAFT`        |
|                   |           | `FINAL`        |
|                   |           | `CANCELLED`    |

</details>

<details>

<summary>Supported event/to-do alarm type</summary>

Additionally, the event or to-do alarm type for a single alarm component can be one of:

* `AUDIO`
* `DISPLAY`
* `EMAIL`

</details>
