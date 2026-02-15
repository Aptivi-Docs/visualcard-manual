---
description: How do you use it?
icon: computer
---

# How to use

VisualCard provides two types of versit types:

* vCard 2.1, 3.0, 4.0, and 5.0
* vCalendar 1.0 and 2.0

{% hint style="info" %}
There are common classes that work on both vCard and vCalendar. They're found in `VisualCard.Common`. There's no need to install it manually, as it's automatically installed as a transitive dependency.
{% endhint %}

***

## <mark style="color:$primary;">vCard 2.1 to 5.0</mark>

Just use the `CardTools` class found in the `VisualCard` namespace that contains all the necessary tools to get a list of cards from either a vCard file, a stream, or a string representation.

{% hint style="info" %}
VisualCard officially supports the vCard 5.0 specification, which can be found [here](https://github.com/Aptivi/VisualCard/blob/main/VisualCard/Specs/vcard-50-aptivi.txt).
{% endhint %}

<details>

<summary>Available functions for obtaining cards</summary>

You can use one of the following functions to obtain cards:

<table><thead><tr><th width="200.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetCardsFromString()</code></td><td>Gets a list of card instances from a string representation of vCard.</td></tr><tr><td><code>GetCards()</code></td><td>Gets a list of card instances from either a file or a stream reader.</td></tr></tbody></table>

These functions return the list of cards from multiple contacts that may be detected by the vCard parser. When parsing is done, it returns an array of `Card` instances that hold information about the contact.

</details>

<details>

<summary>Available functions for saving cards</summary>

To save contacts, call the `SaveTo()` function on a `Card` instance that holds information about a contact you want to save. Currently, it allows you to save using one of the following methods:

<table><thead><tr><th width="159.66668701171875">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>SaveToString()</code></td><td>Saves this contact to a string representation, optionally performing validation before saving.</td></tr><tr><td><code>SaveTo()</code></td><td>Saves this contact to a file path</td></tr></tbody></table>

{% hint style="info" %}
On VCard 4.0 and 5.0, `ALTID` is supported on all the compatible types. You can also group the properties by appending a group name and a dot before the actual property.
{% endhint %}

</details>

***

## <mark style="color:$primary;">vCalendar 1.0 and 2.0</mark>

Additionally, VisualCard can parse calendars, but only after you've installed a separate library, called `VisualCard.Calendar`, that is responsible for handling calendars that are built upon the following vCalendar versions:

* vCalendar 1.0
* vCalendar 2.0

To parse calendars, you can use the `CalendarTools` class.

<details>

<summary>Available functions for obtaining calendars</summary>

You can use one of the following functions to obtain calendars:

<table><thead><tr><th width="229.66668701171875">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetCalendarsFromString()</code></td><td>Gets a list of calendar instances from a string representation of vCalendar.</td></tr><tr><td><code>GetCalendars()</code></td><td>Gets a list of calendar instances from either a file or a stream reader.</td></tr></tbody></table>

These functions return the list of calendars that may be detected by the vCalendar parser. When parsing is done, it returns an array of `Calendar` instances that hold information about the calendar.

</details>

<details>

<summary>Available functions for saving calendars</summary>

Just like vCards, you can also save calendars by calling the `SaveTo()` function on a `Calendar` instance that holds information about a calendar you want to save. Currently, it allows you to save using one of the following methods:

<table><thead><tr><th width="159.66668701171875">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>SaveToString()</code></td><td>Saves this calendar to a string representation, optionally performing validation before saving.</td></tr><tr><td><code>SaveTo()</code></td><td>Saves this calendar to a file path</td></tr></tbody></table>

{% hint style="info" %}
You can group the properties by appending a group name and a dot before the actual property.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Clipboard support</mark>

If you're developing a clipboard manager, you may want to make it detect that it's a vCard or a vCalendar instance using the clipboard object identifier using the `FPI` constant variable in either `CardTools` or `CalendarTools`.

***

## <mark style="color:$primary;">Diagnostics</mark>

You can enable logging for VisualCard by setting the `EnableLogging` property to `true` and by optionally providing the logging provider using the `AbstractLogger` property. To find out more about the internal workings of this feature, consult the below page:

{% content-ref url="https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/ytZJv37OLeFyPEHQJtyw/" %}
[Aptivestigate - Manual](https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/ytZJv37OLeFyPEHQJtyw/)
{% endcontent-ref %}

***

## <mark style="color:$primary;">Spec sheets</mark>

You can see the spec sheets below.

<details>

<summary>vCard</summary>

Each vCard version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF), except that VisualCard also supports vCard 5.0, which is defined by Aptivi:

* [vCard 2.1](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-21.txt)
* [vCard 3.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-30-rfc2426.txt)
* [vCard 4.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-40-rfc6350.txt)
* [vCard 5.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-50-aptivi.txt)

</details>

<details>

<summary>vCalendar</summary>

Each vCalendar version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF):

* [vCalendar 1.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard.Calendar/Specs/vcalendar-10.txt)
* [vCalendar 2.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard.Calendar/Specs/vcalendar-20-rfc5545.txt)

</details>
