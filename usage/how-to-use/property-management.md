---
description: Editing cards and calendars just got easier
icon: pen
---

# Property Management

VisualCard provides you with property management functions that allow editing cards, calendars, and their components, such as calendar alarms, events, journals, and to-dos.

{% hint style="warning" %}
It's recommended to call `Validate()` on cards and/or calendars after you make changes to the property, because all operations (except addition) does not enforce validation.
{% endhint %}

<details>

<summary>Value info overview</summary>

Any function that allows you to get value info of any string or integer property will return an instance of `ValueInfo<string>` or `ValueInfo<double>` that contains the following properties:

<table><thead><tr><th width="139.333251953125">Property</th><th width="106">Editable</th><th>Description</th></tr></thead><tbody><tr><td><code>Arguments</code></td><td>●</td><td>An array of parsed <code>ArgumentInfo</code> instances</td></tr><tr><td><code>AltId</code></td><td>●</td><td>Alternative ID. If it's not specified, it returns <code>-1</code>.</td></tr><tr><td><code>ElementTypes</code></td><td>●</td><td>Card element type (home, work, ...)</td></tr><tr><td><code>Encoding</code></td><td></td><td>Property encoding</td></tr><tr><td><code>Type</code></td><td></td><td>Property type</td></tr><tr><td><code>ValueType</code></td><td></td><td>Value type (usually set by VALUE=)</td></tr><tr><td><code>Group</code></td><td>●</td><td>Property group</td></tr><tr><td><code>NestedGroups</code></td><td></td><td>Nested groups for a property (separated by a dot)</td></tr><tr><td><code>Value</code></td><td>●</td><td>A string or an integer value</td></tr><tr><td><code>IsPreferred</code></td><td></td><td>Is this part preferred?</td></tr></tbody></table>

where `ArgumentInfo` instances contain the following properties and functions:

<table><thead><tr><th width="119.9998779296875">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Key</code></td><td>Argument key name</td></tr><tr><td><code>Values</code></td><td>An array of a tuple that describes the value case sensitivity and the unquoted value</td></tr><tr><td><code>AllValues</code></td><td>An array of unquoted values</td></tr></tbody></table>

You can also use the following functions:

<table><thead><tr><th width="220.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>Arguments.MatchValue()</code></td><td>A function that lets you match a value</td></tr><tr><td><code>HasType()</code></td><td>Checks to see if this value has a specific type</td></tr></tbody></table>

</details>

You can do the following operations on a property:

<details>

<summary>Adding a property</summary>

To add a property to a card and/or a calendar, you can use the following functions:

<table><thead><tr><th width="170.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>AddString()</code></td><td>Adds a string to either a card or a calendar</td></tr><tr><td><code>AddInteger()</code></td><td>Adds an integer to a calendar</td></tr><tr><td><code>AddPartToArray()</code></td><td>Adds a part to either a card or a calendar's part array</td></tr></tbody></table>

The functions all use the following arguments:

* A property type that you want to add
* A raw value that you want to parse (just the value portion of the property delimited by semicolons or commas (depending on a property))
* A group that can be delimited by a dot, an extra prefix to add (only for non-standard properties)
* An array of argument info for passing property parameters, such as `TYPE`, `ALTID`, and so on.

</details>

<details>

<summary>Editing a property</summary>

To edit a property in a card and/or a calendar, you can use any of the functions that allows you to get either a string info, an integer info, or an array info. After that, you can set values to the editable properties.

{% hint style="warning" %}
Because these property value info instances are passed by reference, the edits are instantly saved. You should double check to make sure that you're editing the correct property.
{% endhint %}

</details>

<details>

<summary>Deleting a property</summary>

To delete a property from a card and/or a calendar, you can use the following functions:

<table><thead><tr><th width="179.666748046875">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>DeleteString()</code></td><td>Deletes a string from either a card or a calendar</td></tr><tr><td><code>DeleteInteger()</code></td><td>Deletes an integer from a calendar</td></tr><tr><td><code>DeletePartsArray()</code></td><td>Deletes a part from either a card or a calendar's part array</td></tr></tbody></table>

You'll have to specify the following arguments:

* The property type (either enumeration or type parameter)
* The index of a property that you want to remove.

For example, if you want to remove the third note property from a card, you'll have to specify both `StringsEnum.Notes` and `2` as parameters in the `DeleteString()` function.

</details>

<details>

<summary>Finding a non-standard property</summary>

To find a non-standard property (X-nonstandard and IANA properties) to a card and/or a calendar, you can use the following functions:

<table><thead><tr><th width="210.33343505859375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>FindExtraPartsArray()</code></td><td>Finds non-standard properties of a specified part of property prefix</td></tr></tbody></table>

You'll have to specify the following arguments:

* The property type (either enumeration or type parameter)
* The part of property prefix.

For example, if you have a property called `X-CHARACTERS`, you can just provide `CHAR`, and VisualCard will perform a search.

</details>
