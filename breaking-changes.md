---
description: Listing all the breaking changes.
icon: newspaper
---

# Breaking Changes

There are new releases of VisualCard that cause breaking changes, so you'll need to take them into consideration when upgrading your program to use later versions of VisualCard. Here are the version upgrade paths:

***

## <mark style="color:$primary;">VisualCard v0.x to v1.0</mark>

During the v0.x upgrade to v1.0, you'll need to consider the following:

<details>

<summary>Main ALTID is now <code>-1</code></summary>

The main ALTID number used to be `0`, because you could specify it or not in a property and the ALTID support was half-implemented.

Because of recent improvements to the parsing techniques that VisualCard uses, you can no longer implement some of the different property instances that have its ALTID value of `0`, such as `N` for name information.

All main properties without their positive ALTID values will have their ALTID of `-1`, meaning that it's a main instance.

For example, VisualCard will error out when seeing such properties implemented in a contact's vCard like this:

```
N:Navasquillo;Neville;Neville\,Nevile;Mr.;Jr.
N;ALTID=0;LANGUAGE=de:NAVASQUILLO;Neville;Neville\,Nevile;Mr.;Jr.
```

</details>

<details>

<summary>Enforcing the correct types</summary>

In earlier versions of VisualCard, it allowed any and all of the types, even those that are not supported in all the RFC documents as specified in the [How to use](usage/how-to-use/) page. Starting from VisualCard v1.0, the following base types are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` types

The extra types are written in a separate page, [Card Parts](usage/how-to-use/card-parts.md).

{% hint style="info" %}
If the type that is specified is not supported by a property, such as `warehouse` type in the address property, VisualCard will throw an exception. This will break cards that are generated in a non-standard way.
{% endhint %}

</details>

***

## <mark style="color:$primary;">VisualCard v1.x to v3.0</mark>

During the v1.x upgrade to v3.0, you'll need to consider the following:

<details>

<summary>Moved extra features to VisualCard.Extras</summary>

```csharp
namespace VisualCard.Converters
{
    public static class AndroidContactsDb { }
    public static class MeCard { }
}

namespace VisualCard.Extras
{
    public static class CardGenerator { }
}
```

We've moved extra features that just make use of the VisualCard base library to its own library, `VisualCard.Extras`. As a result, the above classes have been moved to their appropriate namespace defined by that library.

* `VisualCard.Converters` -> `VisualCard.Extras.Converters`
* `VisualCard.Extras` -> `VisualCard.Extras.Misc`

{% hint style="info" %}
You should change the `using` clauses to be able to continue using these extensions.
{% endhint %}

</details>

<details>

<summary><code>MALARM</code> array enum name changed</summary>

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

Due to missing parts from the vCalendar 1.0 original specification text output, we've had to change `NoteAlarm`'s name to `MailAlarm` so that it doesn't mislead developers. As a result, `MALARM` is now considered as a proper alarm with mail as alarm method.

We've also changed the class name like so:

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

</details>

<details>

<summary>Used <code>DateTimeOffset</code> in date-related types</summary>

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

</details>

<details>

<summary>Used periods in <code>RecDateInfo</code></summary>

{% code title="RecDateInfo.cs" lineNumbers="true" %}
```csharp
public DateTimeOffset[]? RecDates { get; }
```
{% endcode %}

Recurrence date information can be get from either a date and time pair or a date/time and a duration string representation. We've used an array of `TimePeriod` instead of `DateTimeOffset` to give better support for vCalendar files that contain recurrence periods.

{% hint style="info" %}
You'll have to get either a start date or an end date from the array, depending on what you're dealing with, to be able to continue using the recurrence date information.
{% endhint %}

</details>

<details>

<summary>Changed how string and integer parts are handled</summary>

{% code title="Card.cs" lineNumbers="true" %}
```csharp
public string GetString(StringsEnum key) { }
```
{% endcode %}

{% code title="Calendar.cs" lineNumbers="true" %}
```csharp
public string GetString(CalendarStringsEnum key) { }
public double GetInteger(CalendarIntegersEnum key) { }
```
{% endcode %}

Amidst the recent improvements that affected how the strings and the integers are returned, we needed to add support for extra properties, type parsing, and value type parsing.

As a result, we've changed these functions so that they return the corresponding ValueInfo classes:

* Cards: `CardValueInfo`
* Calendars: `CalendarValueInfo`

{% hint style="info" %}
Consult the parts documentation for more information as to how to use these class instances.
{% endhint %}

</details>

<details>

<summary><code>ArgumentInfo</code> implemented</summary>

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

`ArgumentInfo` provided a class instance that allowed you to have a better look at the arguments after either a vCard or a vCalendar has been parsed.

The property is still there, but we've changed it to become an array of `ArgumentInfo` so that you can handle the arguments with more care.

As a result, we've removed the `ArgumentValues` property as it's been replaced with the `ArgumentInfo` class instance.

{% hint style="info" %}
You'll need to change how you handle the `Arguments` property, depending on the purpose. If you're using `ArgumentValues`, stop using it and use the `Arguments` property as the latter handles this exact use case.
{% endhint %}

</details>

<details>

<summary>Card kind property changed</summary>

{% code title="Card.cs" lineNumbers="true" %}
```csharp
public string CardKind
```
{% endcode %}

We've introduced the `CardKind` enumeration, so we've decided to make the above property return that enumeration.

{% hint style="info" %}
The string representation is still available, but moved to the `CardKindStr` property.
{% endhint %}

</details>

***

## <mark style="color:$primary;">VisualCard v3.0 to v3.1</mark>

During the v3.0 upgrade to v3.1, you'll need to consider the following:

<details>

<summary><code>PropertyInfo</code> is now more useful</summary>

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

</details>

***

## <mark style="color:$primary;">VisualCard v3.1 to v3.2</mark>

During the v3.1 upgrade to v3.2, you'll need to consider the following:

<details>

<summary><code>CardValueInfo</code> and <code>CalendarValueInfo</code> merged</summary>

{% code title="CardValueInfo.cs" lineNumbers="true" %}
```csharp
public class CardValueInfo<TValue> : IEquatable<CardValueInfo<TValue>>
{
    (...)
}
```
{% endcode %}

{% code title="CalendarValueInfo.cs" lineNumbers="true" %}
```csharp
public class CalendarValueInfo<TValue> : IEquatable<CalendarValueInfo<TValue>>
{
    (...)
}
```
{% endcode %}

We have merged the two above classes into the `ValueInfo` class found in the main VisualCard library as we have spotted common properties that are found in both the above classes. As we want to get rid of redundancy, we've merged them together.

{% hint style="info" %}
You can now use the `ValueInfo` class.
{% endhint %}

</details>

***

## <mark style="color:$primary;">VisualCard v3.2 to v4.0</mark>

During the v3.2 upgrade to v4.0, you'll need to consider the following:

<details>

<summary>Refactored some common code to the common library</summary>

As part of the API refinement that was planned for v4.0, we've migrated the following component-agnostic code to the common library, which is `VisualCard.Common`:

* `ArgumentInfo` \[class]
* `PropertyInfo` \[class]
* `RecurrenceParser` \[class]
* `RecurrenceRule` \[class]
* `RecurrenceRuleFrequency` \[enum]
* `VcardCommonTools` -> `CommonTools` \[class]
* `TimePeriod` \[class]
* `PartType` \[enum]
* `ExtraInfo` \[class]
* `XNameInfo` \[class]
* `ValueInfo` \[class]

In addition to that, we've introduced the `BasePartInfo` that `BaseCardPartInfo` and `BaseCalendarPartInfo` inherit from to reduce code repetition, such as the X-nonstandard and the extra part info classes that are component-agnostic.

{% hint style="info" %}
None of the functions have been removed, so all you have to do is to just update the `using` clause.
{% endhint %}

</details>

<details>

<summary>Separated IANA and non-standard properties</summary>

{% code title="PartsArrayEnum.cs and StringsEnum.cs" lineNumbers="true" %}
```csharp
public enum PartsArrayEnum { }
public enum StringsEnum { }
```
{% endcode %}

We've separated the IANA and the non-standard properties as a result of the above breaking change related to `VisualCard.Common`, because IANA and non-standard properties can be found in both the card and the calendar instances.

{% hint style="danger" %}
You can no longer use the `GetPartsArray()` function and the `PartsArray` property to get IANA and non-standard properties. You should use the `GetExtraPartsArray()` function and the `ExtraParts` property instead.
{% endhint %}

</details>

<details>

<summary>Separated <code>PropertyInfo</code> from <code>ValueInfo</code> and base part classes</summary>

{% code title="PropertyInfo.cs" lineNumbers="true" %}
```csharp
public class PropertyInfo : IEquatable<PropertyInfo?>
```
{% endcode %}

`PropertyInfo` used to hold several property information properties that allowed you to get more information about a property, such as a number of arguments.

Over time, while we were making major structural changes to simplify the codebase, `PropertyInfo` was an obstacle that got in our way, so we had to basically move relevant properties to `ValueInfo` and base part classes.

The following properties have been moved:

* `AltId`
* `Group`
* `NestedGroups`
* `Arguments`
* `Encoding`
* `Type`

{% hint style="info" %}
The above properties have been moved from `ValueInfo`'s `Property` property and from the base part classes' `Property` property, both of which have been removed, to the `ValueInfo` and the base part classes themselves. For example, if you want to get an encoding from `part` that represents one of the two classes, you can now use `part.Encoding` instead of `part.Property?.Encoding`.
{% endhint %}

</details>
