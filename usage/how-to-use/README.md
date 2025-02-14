---
icon: computer
description: How do you use it?
---

# How to use

VisualCard provides two types of versit types:

* vCard 2.1, 3.0, 4.0, and 5.0
* vCalendar 1.0 and 2.0

{% hint style="info" %}
There are common classes that work on both vCard and vCalendar. They're found in `VisualCard.Common`. There's no need to install it manually, as it's automatically installed as a transitive dependency.
{% endhint %}

## vCard 2.1 to 5.0

Just use the `CardTools` class found in the `VisualCard` namespace that contains all the necessayr tools to get a list of cards from either a vCard file, a stream, or a string representation:

* `GetCardsFromString(string)`
* `GetCards(string)`
* `GetCards(StreamReader)`

These functions return the list of cards from multiple contacts that may be detected by the vCard parser. When parsing is done, it returns an array of `Card` instances that hold information about the contact. You can consult the supported parts in the below page:

{% content-ref url="card-parts.md" %}
[card-parts.md](card-parts.md)
{% endcontent-ref %}

{% hint style="info" %}
VisualCard officially supports the vCard 5.0 specification, which can be found [here](https://github.com/Aptivi/VisualCard/blob/main/VisualCard/Specs/vcard-50-aptivi.txt).
{% endhint %}

To save contacts, call the `SaveTo()` function on a `Card` instance that holds information about a contact you want to save. Currently, it allows you to specify the method of saving:

* `SaveTo()`: Saves this contact to a file path
* `SaveToString()`: Saves this contact to a string representation
  * You can pass `true` to this function if you want to validate the card prior to saving

{% hint style="info" %}
On VCard 4.0 and 5.0, `ALTID` is supported on all the compatible types. You can also group the properties by appending a group name and a dot before the actual property.
{% endhint %}

## vCalendar 1.0 and 2.0

Additionally, VisualCard can parse calendars, but only after you've installed a separate library, called `VisualCard.Calendar`, that is responsible for handling calendars that are built upon the following vCalendar versions:

* vCalendar 1.0
* vCalendar 2.0

To parse calendars, you can use the `CalendarTools` class that contains the following functions:

* `GetCalendarsFromString(string)`
* `GetCalendars(string)`
* `GetCalendars(StreamReader)`

These functions return the list of cards from multiple contacts that may be detected by the vCard parser. When parsing is done, it returns an array of `Card` instances that hold information about the contact. You can consult the supported parts in the below page:

{% content-ref url="calendar-card-parts.md" %}
[calendar-card-parts.md](calendar-card-parts.md)
{% endcontent-ref %}

Just like vCards, you can also save calendars by calling the `SaveTo()` function on a `Calendar` instance that holds information about a calendar you want to save. Currently, it allows you to specify the method of saving:

* `SaveTo()`: Saves this calemdar to a file path
* `SaveToString()`: Saves this calendar to a string representation
  * You can pass `true` to this function if you want to validate the card prior to saving

{% hint style="info" %}
You can group the properties by appending a group name and a dot before the actual property.
{% endhint %}

## Clipboard support

If you're developing a clipboard manager, you may want to make it detect that it's a vCard or a vCalendar instance using the clipboard object identifier using the `FPI` constant variable in either `CardTools` or `CalendarTools`.

## Diagnostics

You can enable logging for VisualCard by setting the `EnableLogging` property to `true` and by optionally providing the logging provider using the `AbstractLogger` property. To find out more about the internal workings of this feature, consult the below page:

{% content-ref url="https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/ytZJv37OLeFyPEHQJtyw/" %}
[Aptivestigate - Manual](https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/ytZJv37OLeFyPEHQJtyw/)
{% endcontent-ref %}
