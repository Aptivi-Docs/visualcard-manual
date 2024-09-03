---
description: How do the calendar card parts work in VisualCard?
---

# 📅 Calendar Card Parts

Normally, calendar cards in VisualCard have three types of parts that define a calendar:

* Strings (`GetString()`)
* Integers (`GetInteger()`)
* Array of parts (`GetPartsArray()`)

In the current version of VisualCard, the following parts are supported:

<table><thead><tr><th width="295">Key</th><th width="170">Type</th><th width="59">2.1</th><th width="65">3.0</th><th width="60">4.0</th><th>5.0</th></tr></thead><tbody><tr><td><code>KIND</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>N</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>FN</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TEL</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ADR</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>EMAIL</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ORG</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TITLE</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>URL</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NOTE</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>PHOTO</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>LOGO</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOUND</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>REV</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NICKNAME</code></td><td>Array</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>BDAY</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>MAILER</code></td><td>String</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>ROLE</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>CATEGORIES</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>PRODID</code></td><td>String</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SORT-STRING</code></td><td>String</td><td></td><td>●</td><td></td><td>●</td></tr><tr><td><code>TZ</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>GEO</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>IMPP</code></td><td>Array</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOURCE</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>XML</code></td><td>Array</td><td></td><td></td><td>●</td><td></td></tr><tr><td><code>FBURL</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>CALURI</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>CALADRURI</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>X-NAME</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>AGENT</code></td><td>Array</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>ANNIVERSARY</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>GENDER</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>LANG</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>KEY</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>LABEL</code></td><td>Array</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>CLASS</code></td><td>String</td><td></td><td>●</td><td></td><td>●</td></tr><tr><td><code>UID</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td></td></tr></tbody></table>

The following base types by all the properties that can be put into arrays are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` types

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
