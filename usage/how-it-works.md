---
description: How does it work?
icon: screwdriver
---

# How it works

VisualCard supports contacts and calendars.

## Contacts

When either a string containing a path to the vCard file (`GetCards(string)`) or a string containing the vCard content (`GetCardsFromString(string)`) or a stream containing the vCard content (`GetCards(StreamReader)`) is passed, VisualCard converts the content to a stream first in case we encounter a large vCard file.

VisualCard then attempts to parse all the lines line by line, but first looks for the vCard header at exactly the first line:

```vcard
BEGIN:VCARD
```

Each contact file must begin with the above header, and each contact in a single file must have the begin and the end tags. Parsing fails if omitted.

After the begin tag is spotted, it looks for the version in the exact second line of each contact. If it's either one of:

* `VERSION:2.1`
* `VERSION:3.0`
* `VERSION:4.0`
* `VERSION:5.0`

VisualCard appends the card version to the `CardVersion` property of the parser. VisualCard will then keep adding lines of content until the ending tag is spotted, `END:VCARD`.

Once the ending tag is seen, VisualCard creates a new instance of the `VcardParser` class containing necessary functions to parse the contact, which causes this library to call `Parse()` on the individual contact parser instance which attempts to process all the keys found in the card content, `CardContent`.

The parser first checks to see if the card content is not empty to verify that the builder works right. Once these checks were made, the parser processes each key found. In vCard 4.0 and 5.0, VisualCard takes the ALTID for each supported key with their own cardinality into account. The main ALTID for all the properties is `-1`.

Then, the parser checks the type to see if it is supported by each property type. If the required type is not found, the parser fails. Some of the property types support extra types, such as postal address, IBM Mail e-mail address, and so on.

Once the parser finishes installing all the values from all the supported keys, VisualCard checks for the below requirements:

| vCard     | Name (N) | Full name (FN) |
| --------- | -------- | -------------- |
| vCard 2.1 | ●        |                |
| vCard 3.0 | ●        | ●              |
| vCard 4.0 |          | ●              |
| vCard 5.0 | ●        | ●              |

If the requirements are met, VisualCard returns a new `Card` instance that you can fetch its values from using one of the following methods:

* `GetPartsArray()`
* `GetString()`

## Spec sheets

Each vCard version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF), except that VisualCard also supports vCard 5.0, which is defined by Aptivi:

* [vCard 2.1](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-21.txt)
* [vCard 3.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-30-rfc2426.txt)
* [vCard 4.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-40-rfc6350.txt)
* [vCard 5.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-50-aptivi.txt)

## Calendars

When either a string containing a path to the vCalendar file (`GetCalendars(string)`) or a string containing the vCalendar content (`GetCalendarsFromString(string)`) or a stream containing the vCalendar content (`GetCalendars(StreamReader)`) is passed, VisualCard converts the content to a stream first in case we encounter a large vCalendar file.

VisualCard then attempts to parse all the lines line by line, but first looks for the vCalendar header at exactly the first line:

```vcard
BEGIN:VCALENDAR
```

Each calendar file must begin with the above header, and each contact in a single file must have the begin and the end tags. Parsing fails if omitted.

After the begin tag is spotted, it looks for the version in the root property list before any event, to-do, alarm, free/busy, or journal. If it's either one of:

* `VERSION:1.0`
* `VERSION:2.0`

VisualCard appends the calendar version to the `CalendarVersion` property of the parser. VisualCard will then keep adding lines of content until the ending tag is spotted, `END:VCALENDAR`.

Once the ending tag is seen, VisualCard creates a new instance of the `VCalendarParser` class containing necessary functions to parse the calendar, which causes this library to call `Parse()` on the individual calendar parser instance which attempts to process all the keys found in the calendar content, `CalendarContent`.

The parser first checks to see if the calendar content is not empty to verify that the builder works right. Once these checks were made, the parser processes each key found. Then, the parser checks the type to see if it is supported by each property type. If the required type is not found, the parser fails.

Once the parser finishes installing all the values from all the supported keys, VisualCard checks for the below requirements:

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

If the requirements are met, VisualCard returns a new `Calendar` instance that you can fetch its values from using one of the following methods:

* `GetPartsArray()`
* `GetInteger()`
* `GetString()`

## Spec sheets

Each vCalendar version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF):

* [vCalendar 1.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard.Calendar/Specs/vcalendar-10.txt)
* [vCalendar 2.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt)
