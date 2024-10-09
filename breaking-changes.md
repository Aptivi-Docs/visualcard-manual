---
icon: newspaper
description: Listing all the breaking changes.
---

# Breaking Changes

There are new releases of VisualCard that cause breaking changes, so you'll need to take them into consideration when upgrading your program to use later versions of VisualCard. Here are the version upgrade paths:

## VisualCard v0.x to v1.0

During the v0.x upgrade to v1.0, you'll need to consider the following:

### Main ALTID is now `-1`

The main ALTID number used to be `0`, because you could specify it or not in a property and the ALTID support was half-implemented. Now, because of the recent improvements to the parsing techniques that VisualCard uses, you can no longer implement some of the different property instances that have its ALTID value of `0`, such as `N` for name information. All main properties without their positive ALTID values will have their ALTID of `-1`, meaning that it's a main instance. For example, VisualCard will error out when seeing such properties implemented in a contact's vCard like this:

```
N:Navasquillo;Neville;Neville\,Nevile;Mr.;Jr.
N;ALTID=0;LANGUAGE=de:NAVASQUILLO;Neville;Neville\,Nevile;Mr.;Jr.
```

### Enforcing the correct types

In earlier versions of VisualCard, it allowed any and all of the types, even those that are not supported in all the RFC documents as specified in the [How to use](usage/how-to-use/) page. Starting from VisualCard v1.0, the following base types are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` types

The extra types are written in a separate page, [Card Parts](usage/how-to-use/card-parts.md).

If the type that is specified is not supported by a property, such as `warehouse` type in the address property, VisualCard will throw an exception. This will break cards that are generated in a non-standard way.

## VisualCard v1.x to v3.0

During the v1.x upgrade to v3.0, you'll need to consider the following:

### Moved extra features to VisualCard.Extras

```csharp
namespace VisualCard.Converters
{
    public static class AndroidContactsDb
    public static class MeCard
}

namespace VisualCard.Extras
{
    public static class CardGenerator
}
```

We've moved extra features that just make use of the VisualCard base library to its own library, `VisualCard.Extras`. As a result, the above classes have been moved to their appropriate namespace defined by that library.

* `VisualCard.Converters` -> `VisualCard.Extras.Converters`
* `VisualCard.Extras` -> `VisualCard.Extras.Misc`

{% hint style="info" %}
You should change the `using` clauses to be able to continue using these extensions.
{% endhint %}

### `MALARM` array enum name changed

{% code title="CalendarPartsArrayEnum.cs" lineNumbers="true" %}
```csharp
public enum CalendarPartsArrayEnum
{
    (...)
    NoteAlarm,
    (...)
}
```
{% endcode %}

Due to missing parts from the vCalendar 1.0 original specification text output, we've had to change `NoteAlarm`'s name to `MailAlarm` so that it doesn't mislead developers. As a result, `MALARM` is now considered as a proper alarm with mail as alarm method. We've also changed the class name like so:

{% code title="MailAlarmInfo.cs" lineNumbers="true" %}
```diff
- public class NoteAlarmInfo : BaseCalendarPartInfo, IEquatable<NoteAlarmInfo>
+ public class MailAlarmInfo : BaseCalendarPartInfo, IEquatable<MailAlarmInfo>
```
{% endcode %}

{% hint style="info" %}
You should change all references to the `NoteAlarmInfo` class and to the `NoteAlarm` enum value so that they point to the following:

* `CalendarPartsArrayEnum.MailAlarm`
* `MailAlarmInfo`
{% endhint %}

### Used `DateTimeOffset` in date-related types

{% code title="AnniversaryInfo.cs" lineNumbers="true" %}
```csharp
// This also applies to all type instances that used DateTime
public DateTime Anniversary { get; }
```
{% endcode %}

We've changed the date definitions from `DateTime` to `DateTimeOffset` as there is confusion when dealing with time offsets as explained [here](https://stackoverflow.com/questions/4331189/datetime-vs-datetimeoffset). VisualCard deals with date and time which may be described as local time according to a specific time zone.

{% hint style="info" %}
You don't need to do anything unless you do something that breaks the property call.
{% endhint %}

### Used periods in `RecDateInfo`

{% code title="RecDateInfo.cs" lineNumbers="true" %}
```csharp
public DateTimeOffset[]? RecDates { get; }
```
{% endcode %}

Recurrence date information can be get from either a date and time pair or a date/time and a duration string representation. We've used an array of `TimePeriod` instead of `DateTimeOffset` to give better support for vCalendar files that contain recurrence periods.

{% hint style="info" %}
You'll have to get either a start date or an end date from the array, depending on what you're dealing with, to be able to continue using the recurrence date information.
{% endhint %}

### Changed how string and integer parts are handled

{% code title="Card.cs" lineNumbers="true" %}
```csharp
public string GetString(StringsEnum key)
```
{% endcode %}

{% code title="Calendar.cs" lineNumbers="true" %}
```csharp
public string GetString(CalendarStringsEnum key)
public double GetInteger(CalendarIntegersEnum key)
```
{% endcode %}

Amidst the recent improvements that affected how the strings and the integers are returned, we needed to add support for extra properties, type parsing, and value type parsing. As a result, we've changed these functions so that they return the corresponding ValueInfo classes:

* Cards: `CardValueInfo`
* Calendars: `CalendarValueInfo`

{% hint style="info" %}
Consult the parts documentation for more information as to how to use these class instances.
{% endhint %}

### `ArgumentInfo` implemented

{% code title="BaseCardPartInfo.cs" lineNumbers="true" %}
```csharp
public virtual string[] Arguments { get; internal set; } = [];
```
{% endcode %}

{% code title="BaseCalendarPartInfo.cs" lineNumbers="true" %}
```csharp
public virtual string[]? Arguments { get; internal set; }
```
{% endcode %}

`ArgumentInfo` provided a class instance that allowed you to have a better look at the arguments after either a vCard or a vCalendar has been parsed. The property is still there, but we've changed it to become an array of `ArgumentInfo` so that you can handle the arguments with more care.

As a result, we've removed the `ArgumentValues` property as it's been replaced with the `ArgumentInfo` class instance.

{% hint style="info" %}
You'll need to change how you handle the `Arguments` property, depending on the purpose. If you're using `ArgumentValues`, stop using it and use the `Arguments` property as the latter handles this exact use case.
{% endhint %}

### Card kind property changed

{% code title="Card.cs" lineNumbers="true" %}
```csharp
public string CardKind
```
{% endcode %}

We've introduced the `CardKind` enumeration, so we've decided to make the above property return that enumeration.

{% hint style="info" %}
The string representation is still available, but moved to the `CardKindStr` property.
{% endhint %}

## VisualCard v3.0 to v3.1

During the v3.0 upgrade to v3.1, you'll need to consider the following:

### `PropertyInfo` is now more useful

{% code title="Base*PartInfo.cs / *ValueInfo.cs" lineNumbers="true" %}
```csharp
public virtual ArgumentInfo[] Arguments { get; internal set; } = [];
```
{% endcode %}

The following classes are affected with this change:

* `BaseCardPartInfo`
* `CardValueInfo`
* `BaseCalendarPartInfo`
* `CalendarValueInfo`

The above property has been edited so that it points to the relevant `PropertyInfo` instance that contains the `Arguments` property, which has exactly the same amount of information that you'd obtain from there.

{% hint style="info" %}
To be able to access this property, you need to access the `Property` value in a card part or a value info class.
{% endhint %}
