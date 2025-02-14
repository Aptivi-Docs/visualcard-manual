---
icon: pen
description: Editing cards and calendars just got easier
---

# Property Management

VisualCard provides you with property management functions that allow editing cards, calendars, and their components, such as calendar alarms, events, journals, and to-dos. You can do the following:

* Adding a property
* Editing a property
* Deleting a property
* Finding a non-standard property

{% hint style="warning" %}
It's recommended to call `Validate()` on cards and/or calendars after you make changes to the property, because all operations (except addition) does not enforce validation.
{% endhint %}

## Value info

Any function that allows you to get value info of any string or integer property will return an instance of `ValueInfo<string>` or `ValueInfo<double>` that contains the following properties: (Any property marked in <mark style="color:green;">green</mark> means editable)

* <mark style="color:green;">`Arguments`</mark>: An array of parsed `ArgumentInfo` instances that contains the following properties and functions:
  * `Key`: Argument key name
  * `Values`: An array of a tuple that describes the value case sensitivity and the unquoted value
  * `AllValues`: An array of unquoted values
* <mark style="color:green;">`AltId`</mark>: Alternative ID. If it's not specified, it returns `-1`.
* <mark style="color:green;">`ElementTypes`</mark>: Card element type (home, work, ...)
* `Encoding`: Property encoding
* `Type`: Property type
* `ValueType`: Value type (usually set by VALUE=)
* <mark style="color:green;">`Group`</mark>: Property group
* `NestedGroups`: Nested groups for a property (separated by a dot)
* <mark style="color:green;">`Value`</mark>: A string or an integer value
* `IsPreferred`: Is this part preferred?

You can also use the following functions:

* `Arguments.MatchValue()`: A function that lets you match a value
* `HasType()`: Checks to see if this value has a specific type

## Adding a property

To add a property to a card and/or a calendar, you can use the following functions:

* `AddString()`: Adds a string to either a card or a calendar
* `AddInteger()`: Adds an integer to a calendar
* `AddPartToArray()`: Adds a part to either a card or a calendar's part array

The functions all use the property type that you want to add, a raw value that you want to parse (just the value portion of the property delimited by semicolons or commas (depending on a property)), a group that can be delimited by a dot, an extra prefix to add (only for non-standard properties), and an array of argument info for passing property parameters, such as `TYPE`, `ALTID`, and so on.

## Editing a property

To edit a property in a card and/or a calendar, you can use any of the functions that allows you to get either a string info, an integer info, or an array info. After that, you can set values to the above properties that are marked as green.

{% hint style="warning" %}
Because these property value info instances are passed by reference, the edits are instantly saved. You should double check to make sure that you're editing the correct property.
{% endhint %}

## Deleting a property

To delete a property from a card and/or a calendar, you can use the following functions:

* `DeleteString()`: Deletes a string from either a card or a calendar
* `DeleteInteger()`: Deletes an integer from a calendar
* `DeletePartsArray()`: Deletes a part from either a card or a calendar's part array

You'll have to specify the property type (either enumeration or type parameter), and you'll have to determine the index of a property that you want to remove. For example, if you want to remove the third note property from a card, you'll have to specify both `StringsEnum.Notes` and `2` as parameters in the `DeleteString()` function.

## Finding a non-standard property

To find a non-standard property (X-nonstandard and IANA properties) to a card and/or a calendar, you can use the following functions:

* `FindExtraPartsArray()`: Finds non-standard properties of a specified part of property prefix

You'll have to specify the property type (either enumeration or type parameter), and you'll have to qrite part of property prefix. For example, if you have a property called `X-CHARACTERS`, you can just provide `CHAR`, and VisualCard will perform a search.
