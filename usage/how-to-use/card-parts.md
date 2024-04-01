---
description: How do the card parts work in VisualCard?
---

# 🧩 Card Parts

Normally, cards in VisualCard have three types of parts that define a contact:

* Strings (`GetString()`)
* Parts (`GetPart()`)
* Array of parts (`GetPartsArray()`)

In the current version of VisualCard, the following parts are supported:

| Key           | Type   | 2.1 | 3.0 | 4.0 | 5.0 |
| ------------- | ------ | --- | --- | --- | --- |
| `KIND`        | String |     |     | ●   | ●   |
| `N`           | Array  | ●   | ●   | ●   | ●   |
| `FN`          | String | ●   | ●   | ●   | ●   |
| `TEL`         | Array  | ●   | ●   | ●   | ●   |
| `ADR`         | Array  | ●   | ●   | ●   | ●   |
| `EMAIL`       | Array  | ●   | ●   | ●   | ●   |
| `ORG`         | Array  | ●   | ●   | ●   | ●   |
| `TITLE`       | Array  | ●   | ●   | ●   | ●   |
| `URL`         | String | ●   | ●   | ●   | ●   |
| `NOTE`        | String | ●   | ●   | ●   | ●   |
| `PHOTO`       | Array  | ●   | ●   | ●   | ●   |
| `LOGO`        | Array  | ●   | ●   | ●   | ●   |
| `SOUND`       | Array  | ●   | ●   | ●   | ●   |
| `REV`         | Part   | ●   | ●   | ●   | ●   |
| `NICKNAME`    | Array  |     | ●   | ●   | ●   |
| `BDAY`        | Part   | ●   | ●   | ●   | ●   |
| `MAILER`      | String | ●   | ●   |     | ●   |
| `ROLE`        | Array  | ●   | ●   | ●   | ●   |
| `CATEGORIES`  | Array  | ●   | ●   | ●   | ●   |
| `PRODID`      | String |     | ●   | ●   | ●   |
| `SORT-STRING` | String |     | ●   |     | ●   |
| `TZ`          | Array  | ●   | ●   | ●   | ●   |
| `GEO`         | Array  | ●   | ●   | ●   | ●   |
| `IMPP`        | Array  |     | ●   | ●   | ●   |
| `SOURCE`      | String | ●   | ●   | ●   | ●   |
| `XML`         | Array  |     |     | ●   |     |
| `FBURL`       | String |     |     | ●   | ●   |
| `CALURI`      | String |     |     | ●   | ●   |
| `CALADRURI`   | String |     |     | ●   | ●   |
| `X-NAME`      | Array  | ●   | ●   | ●   | ●   |
| `AGENT`       | Array  | ●   | ●   |     | ●   |
| `ANNIVERSARY` | Part   |     |     | ●   | ●   |
| `GENDER`      | Part   |     |     | ●   | ●   |
| `LANG`        | Array  |     |     | ●   | ●   |
| `KEY`         | Array  | ●   | ●   | ●   | ●   |
| `LABEL`       | Array  | ●   | ●   |     | ●   |
| `CLASS`       | String |     | ●   |     | ●   |

The below sections describe how exactly to parse all the supported types.

## Strings

Strings in vCard and VisualCard are the simplest of the types that allow you to input just text that represent that property. The above table shows all the properties, and those that are listed as a String, such as `CLASS`, can be get as a string using a function called `GetString()`.

This function returns one of the following strings:

* **An empty string**
  * If the string is not supported in the contact's vCard version.
  * If the string is not defined in the contact's vCard instance.
  * If the string is explicitly blank.
* **"individual"**
  * If the string is not defined in the contact's vCard 4.0 or 5.0 kind.
  * If the string is explicitly "individual" in the contact's vCard 4.0 or 5.0 kind.
* **A string value**
  * If the string is defined, supported, and is not empty.

## Parts

Parts that can't be more than one part (i.e. can't be put to an array and can only exist once per vCard instance) exist in vCard. The above table shows all the properties that are listed as a Part. If they are listed as such, like `REV`, you can get it using `GetPart()`.

`GetPart()` is a generic method. This means that you can specify one of the `Info` classes, as long as it represents a valid class that points to a valid part, such as `RevisionInfo`. In this case, you'll have to call it like this:

```csharp
// Either
Contact.GetPart<RevisionInfo>()

// or
Contact.GetPart<RevisionInfo>(PartsEnum.Revision)
```

You can directly get a value of a property without having to cast the resultant part to the correct part info class. The following base properties are available for every part:

* `Arguments`
* `AltId`
* `ElementTypes`
* `ValueType`

{% hint style="info" %}
You can also get any part as a base, though you can't call the non-parameterized function against the base part, `BaseCardPartInfo`. You'll also have to cast the resultant part if you need to access something other than the base properties as mentioned above.

```csharp
Contact.GetPart<BaseCardPartInfo>(PartsEnum.Revision)
```
{% endhint %}

This function returns one of the following:

* **`null`**
  * If the part is not supported in the contact's vCard version
  * If the part is not defined in the contact's vCard instance
* **A part instance**
  * If the part is supported and defined in the contact's vCard instance

{% hint style="danger" %}
Any attempt to specify an incorrect type or enumeration in the second overload of `GetPart`, such as `Contact.GetPart<RevisionInfo>(PartsEnum.Anniversary)`, will throw an exception. However, it doesn't throw an exception in case `BaseCardPartInfo` is specified.
{% endhint %}

## Array of Parts

Parts that can be more than one part (i.e. can be put to an array and can exist more than once per vCard instance) exist in vCard. The above table shows all the properties that are listed as an Array. If they are listed as such, like `TEL`, you can get it using `GetPartsArray()`.

`GetPartsArray()` is a generic method. This means that you can specify one of the `Info` classes, as long as it represents a valid class that points to a valid part, such as `TelephoneInfo`. In this case, you'll have to call it like this:

```csharp
// Either
Contact.GetPartsArray<TelephoneInfo>()

// or
Contact.GetPartsArray<TelephoneInfo>(PartsArrayEnum.Telephone)
```

You can directly get a value of a property without having to cast the resultant part to the correct part info class. The same base properties also apply to the normal Parts.

{% hint style="info" %}
You can also get any parts array as a base, though you can't call the non-parameterized function against the base part, `BaseCardPartInfo`. You'll also have to cast the resultant part if you need to access something other than the base properties as mentioned above.

```csharp
Contact.GetPartsArray<BaseCardPartInfo>(PartsArrayEnum.Telephone)
```
{% endhint %}

This function returns one of the following:

* **An empty array**
  * If the parts array is not supported in the contact's vCard version
  * If the parts array is not defined in the contact's vCard instance
* **An array of parts**
  * If the part is supported and defined in the contact's vCard instance

{% hint style="danger" %}
Any attempt to specify an incorrect type or enumeration in the second overload of `GetPartsArray`, such as `Contact.GetPartsArray<AddressInfo>(PartsArrayEnum.Telephone)`, will throw an exception. However, it doesn't throw an exception in case `BaseCardPartInfo` is specified.
{% endhint %}
