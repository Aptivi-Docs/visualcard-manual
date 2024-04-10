---
description: How do the card parts work in VisualCard?
---

# 🧩 Card Parts

Normally, cards in VisualCard have three types of parts that define a contact:

* Strings (`GetString()`)
* Array of parts (`GetPartsArray()`)

In the current version of VisualCard, the following parts are supported:

| Key           | Type   | 2.1 | 3.0 | 4.0 | 5.0 |
| ------------- | ------ | --- | --- | --- | --- |
| `KIND`        | String |     |     | ●   | ●   |
| `N`           | Array  | ●   | ●   | ●   | ●   |
| `FN`          | Array  | ●   | ●   | ●   | ●   |
| `TEL`         | Array  | ●   | ●   | ●   | ●   |
| `ADR`         | Array  | ●   | ●   | ●   | ●   |
| `EMAIL`       | Array  | ●   | ●   | ●   | ●   |
| `ORG`         | Array  | ●   | ●   | ●   | ●   |
| `TITLE`       | Array  | ●   | ●   | ●   | ●   |
| `URL`         | Array  | ●   | ●   | ●   | ●   |
| `NOTE`        | Array  | ●   | ●   | ●   | ●   |
| `PHOTO`       | Array  | ●   | ●   | ●   | ●   |
| `LOGO`        | Array  | ●   | ●   | ●   | ●   |
| `SOUND`       | Array  | ●   | ●   | ●   | ●   |
| `REV`         | Array  | ●   | ●   | ●   | ●   |
| `NICKNAME`    | Array  |     | ●   | ●   | ●   |
| `BDAY`        | Array  | ●   | ●   | ●   | ●   |
| `MAILER`      | String | ●   | ●   |     | ●   |
| `ROLE`        | Array  | ●   | ●   | ●   | ●   |
| `CATEGORIES`  | Array  | ●   | ●   | ●   | ●   |
| `PRODID`      | String |     | ●   | ●   | ●   |
| `SORT-STRING` | String |     | ●   |     | ●   |
| `TZ`          | Array  | ●   | ●   | ●   | ●   |
| `GEO`         | Array  | ●   | ●   | ●   | ●   |
| `IMPP`        | Array  |     | ●   | ●   | ●   |
| `SOURCE`      | Array  | ●   | ●   | ●   | ●   |
| `XML`         | Array  |     |     | ●   |     |
| `FBURL`       | Array  |     |     | ●   | ●   |
| `CALURI`      | Array  |     |     | ●   | ●   |
| `CALADRURI`   | Array  |     |     | ●   | ●   |
| `X-NAME`      | Array  | ●   | ●   | ●   | ●   |
| `AGENT`       | Array  | ●   | ●   |     | ●   |
| `ANNIVERSARY` | Array  |     |     | ●   | ●   |
| `GENDER`      | Array  |     |     | ●   | ●   |
| `LANG`        | Array  |     |     | ●   | ●   |
| `KEY`         | Array  | ●   | ●   | ●   | ●   |
| `LABEL`       | Array  | ●   | ●   |     | ●   |
| `CLASS`       | String |     | ●   |     | ●   |

The following base types by all the properties that can be put into arrays are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` types
* Extra types supported by some properties, such as `ADR` and `TEL`

Here are the extra types that the following properties support:

<table><thead><tr><th width="128">Property</th><th>Types</th></tr></thead><tbody><tr><td><code>TEL</code></td><td>"<code>TEXT</code>", "<code>VOICE</code>", "<code>FAX</code>", "<code>CELL</code>", "<code>VIDEO</code>", "<code>PAGER</code>", "<code>TEXTPHONE</code>", "<code>ISDN</code>", "<code>CAR</code>", "<code>MODEM</code>", "<code>BBS</code>", "<code>MSG</code>", "<code>PREF</code>", "<code>TLX</code>", "<code>MMS</code>"</td></tr><tr><td><code>ADR</code></td><td>"<code>DOM</code>", "<code>INTL</code>", "<code>PARCEL</code>", "<code>POSTAL</code>"</td></tr><tr><td><code>LABEL</code></td><td>"<code>DOM</code>", "<code>INTL</code>", "<code>PARCEL</code>", "<code>POSTAL</code>"</td></tr><tr><td><code>EMAIL</code></td><td>"<code>AOL</code>", "<code>APPLELINK</code>", "<code>ATTMAIL</code>", "<code>CIS</code>", "<code>EWORLD</code>", "<code>INTERNET</code>", "<code>IBMMAIL</code>", "<code>MCIMAIL</code>", "<code>POWERSHARE</code>", "<code>PRODIGY</code>", "<code>TLX</code>", "<code>X400</code>", "<code>CELL</code>"</td></tr><tr><td><code>PHOTO</code></td><td>"<code>JPG</code>", "<code>GIF</code>", "<code>CGM</code>", "<code>WMF</code>", "<code>BMP</code>", "<code>MET</code>", "<code>PMB</code>", "<code>DIB</code>", "<code>PICT</code>", "<code>TIFF</code>", "<code>PS</code>", "<code>PDF</code>", "<code>JPEG</code>", "<code>MPEG</code>", "<code>MPEG2</code>", "<code>AVI</code>", "<code>QTIME</code>", "<code>PNG</code>", "<code>WEBP</code>"</td></tr><tr><td><code>LOGO</code></td><td>"<code>JPG</code>", "<code>GIF</code>", "<code>CGM</code>", "<code>WMF</code>", "<code>BMP</code>", "<code>MET</code>", "<code>PMB</code>", "<code>DIB</code>", "<code>PICT</code>", "<code>TIFF</code>", "<code>PS</code>", "<code>PDF</code>", "<code>JPEG</code>", "<code>MPEG</code>", "<code>MPEG2</code>", "<code>AVI</code>", "<code>QTIME</code>", "<code>PNG</code>", "<code>WEBP</code>"</td></tr><tr><td><code>SOUND</code></td><td>"<code>MP3</code>", "<code>WAVE</code>", "<code>PCM</code>", "<code>AIFF</code>", "<code>AAC</code>"</td></tr><tr><td><code>IMPP</code></td><td>"<code>SIP</code>"</td></tr></tbody></table>

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
