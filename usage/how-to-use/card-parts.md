---
icon: puzzle-piece
description: How do the card parts work in VisualCard?
---

# Card Parts

Normally, cards in VisualCard have two types of parts that define a contact:

* Strings (`Strings` property and `GetString()` function)
* Array of parts (`PartsArray` property and `GetPartsArray()` function)

In the current version of VisualCard, the following parts are supported:

<table><thead><tr><th width="295">Key</th><th width="170">Type</th><th width="59">2.1</th><th width="65">3.0</th><th width="60">4.0</th><th>5.0</th></tr></thead><tbody><tr><td><code>KIND</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>N</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>FN</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TEL</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ADR</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>EMAIL</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ORG</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TITLE</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>URL</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NOTE</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>PHOTO</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>LOGO</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOUND</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>REV</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NICKNAME</code></td><td>String</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>BDAY</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>MAILER</code></td><td>String</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>ROLE</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>CATEGORIES</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>PRODID</code></td><td>String</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SORT-STRING</code></td><td>String</td><td></td><td>●</td><td></td><td>●</td></tr><tr><td><code>TZ</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>GEO</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>IMPP</code></td><td>String</td><td></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOURCE</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>XML</code></td><td>Array</td><td></td><td></td><td>●</td><td></td></tr><tr><td><code>FBURL</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>CALURI</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>CALADRURI</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>X-NAME</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>AGENT</code></td><td>Array</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>ANNIVERSARY</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>GENDER</code></td><td>Array</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>LANG</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>KEY</code></td><td>Array</td><td>●</td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>LABEL</code></td><td>String</td><td>●</td><td>●</td><td></td><td>●</td></tr><tr><td><code>CLASS</code></td><td>String</td><td></td><td>●</td><td></td><td>●</td></tr><tr><td><code>UID</code></td><td>String</td><td>●</td><td>●</td><td>●</td><td></td></tr><tr><td><code>CONTACT-URI</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>MEMBER</code></td><td>String</td><td></td><td></td><td>●</td><td></td></tr><tr><td><code>RELATED</code></td><td>String</td><td></td><td></td><td>●</td><td></td></tr><tr><td><code>CLIENTPIDMAP</code></td><td>Array</td><td></td><td></td><td>●</td><td></td></tr><tr><td><code>NAME</code></td><td>String</td><td></td><td>●</td><td></td><td></td></tr><tr><td><code>PROFILE</code></td><td>String</td><td></td><td>●</td><td></td><td></td></tr><tr><td><code>EXPERTISE</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>HOBBY</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>INTEREST</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr><tr><td><code>ORG-DIRECTORY</code></td><td>String</td><td></td><td></td><td>●</td><td>●</td></tr></tbody></table>

The following base types by all the properties that can be put into arrays are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` and IANA types
* Extra types supported by some properties, such as `ADR` and `TEL`

Here are the extra types that the following properties support:

<table><thead><tr><th width="128">Property</th><th>Types</th></tr></thead><tbody><tr><td><code>TEL</code></td><td><code>TEXT</code>, <code>VOICE</code>, <code>FAX</code>, <code>CELL</code>, <code>VIDEO</code>, <code>PAGER</code>, <code>TEXTPHONE</code>, <code>ISDN</code>, <code>CAR</code>, <code>MODEM</code>, <code>BBS</code>, <code>MSG</code>, <code>PREF</code>, <code>TLX</code>, <code>MMS</code></td></tr><tr><td><code>ADR</code></td><td><code>DOM</code>, <code>INTL</code>, <code>PARCEL</code>, <code>POSTAL</code></td></tr><tr><td><code>LABEL</code></td><td><code>DOM</code>, <code>INTL</code>, <code>PARCEL</code>, <code>POSTAL</code></td></tr><tr><td><code>EMAIL</code></td><td><code>AOL</code>, <code>APPLELINK</code>, <code>ATTMAIL</code>, <code>CIS</code>, <code>EWORLD</code>, <code>INTERNET</code>, <code>IBMMAIL</code>, <code>MCIMAIL</code>, <code>POWERSHARE</code>, <code>PRODIGY</code>, <code>TLX</code>, <code>X400</code>, <code>CELL</code></td></tr><tr><td><code>PHOTO</code></td><td><code>JPG</code>, <code>GIF</code>, <code>CGM</code>, <code>WMF</code>, <code>BMP</code>,<code>MET</code>, <code>PMB</code>, <code>DIB</code>, <code>PICT</code>, <code>TIFF</code>, <code>PS</code>, <code>PDF</code>, <code>JPEG</code>, <code>MPEG</code>, <code>MPEG2</code>, <code>AVI</code>, <code>QTIME</code>, <code>PNG</code>, <code>WEBP</code></td></tr><tr><td><code>LOGO</code></td><td><code>JPG</code>, <code>GIF</code>, <code>CGM</code>, <code>WMF</code>, <code>BMP</code>, <code>MET</code>, <code>PMB</code>, <code>DIB</code>, <code>PICT</code>, <code>TIFF</code>, <code>PS</code>, <code>PDF</code>, <code>JPEG</code>, <code>MPEG</code>, <code>MPEG2</code>, <code>AVI</code>, <code>QTIME</code>, <code>PNG</code>, <code>WEBP</code></td></tr><tr><td><code>SOUND</code></td><td><code>MP3</code>, <code>WAVE</code>, <code>PCM</code>, <code>AIFF</code>, <code>AAC</code></td></tr><tr><td><code>IMPP</code></td><td><code>SIP</code></td></tr></tbody></table>

The below sections describe how exactly to parse all the supported types.

{% hint style="info" %}
You can access all extra X-named and IANA properties by calling `GetExtraPartsArray`, passing it either the `XNameInfo` or the `ExtraInfo` type as a generic type argument.
{% endhint %}

## Strings

Strings in vCard and VisualCard are the simplest of the types that allow you to input just text that represent that property. The above table shows all the properties, and those that are listed as a String, such as `CLASS`, can be get as a string using a function called `GetString()`. You can also get a dictionary of a list of parsed strings using the `Strings` property.

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

{% hint style="info" %}
You can easily access the card kind using the `CardKindStr` property from a card instance. It's also available as an enumeration value via the `CardKind` property.
{% endhint %}

When using the above function, it returns an instance of `ValueInfo<string>` that contains the following properties:

* `Property`: An instance of `PropertyInfo` that shows you a dissection of raw prefix, group, and values. It contains the following properties:
  * `Arguments`: An array of parsed `ArgumentInfo` instances that contains the following properties and functions:
    * `Key`: Argument key name
    * `Values`: An array of a tuple that describes the value case sensitivity and the unquoted value
    * `AllValues`: An array of unquoted values
    * `MatchValue()`: A function that lets you match a value
  * `Value`: Raw value, as it appears on a vCard representation
  * `Prefix`: Raw prefix, as it appears on a vCard representation
  * `Group`: Raw group, as it appears on a vCard representation
  * `NestedGroups`: Nested groups separated by a dot
  * `Encoding`: Property encoding
  * `Type`: Property type
  * `ValueType`: Property value type
* `AltId`: Alternative ID. If it's not specified, it returns `-1`.
* `ElementTypes`: Card element type (home, work, ...)
* `ValueType`: Value type (usually set by VALUE=)
* `Group`: Property group
* `NestedGroups`: Nested groups for a property (separated by a dot)
* `Value`: A string value
* `IsPreferred`: Is this part preferred?

You can also use the following functions:

* `HasType()`: Checks to see if this value has a specific type

You can also specify the encoding of `QUOTED-PRINTABLE` to enable support for Unicode characters that may get decoded.

## Array of Parts

Parts that can be more than one part (i.e. can be put to an array and can exist more than once per vCard instance) exist in vCard. The above table shows all the properties that are listed as an Array. If they are listed as such, like `TEL`, you can get it using `GetPartsArray()`. You can also get a dictionary of a list of parsed parts array lists using the `PartsArray` property.

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

For preferred parts, their value of the `IsPreferred` property is true, assuming that the `PREF` type exists in such parts.

You can also specify the encoding of `QUOTED-PRINTABLE` to enable support for Unicode characters that may get decoded.

## Getting a Blob Stream

Image parts, icon parts, sound parts, and key parts in a vCard instance allow you to get a blob stream from the encoded data that allows you to represent the actual data decoded from the BASE64 encoding as a blob. VisualCard exposes this feature to allow you to perform various operations on them, such as displaying contact pictures, saving sound parts as sound files, etc.

You can make use of this feature by invoking the `GetBlobData()` function from the `VcardParserTools` class.

{% hint style="danger" %}
This feature doesn't support non-blob values, such as an HTTPS URL to a logo file.
{% endhint %}

## Nested cards

Sometimes, you may come across a vCard file that consists of multiple nested vCards. This, accompanied with the `UID` property, can be connected so that you can make relationships with cards. You can easily access all children cards within a property in your `Card` instance using a property called `NestedCards`. You can easily access the UID of a card via a `UniqueId` property.

{% hint style="warning" %}
When no `UID` property is specified in the vCard file, it's empty, so it's assumed to have no relationship with any card. Even if they have no UID, they can be nested.
{% endhint %}

In addition to accessing all nested cards, you can also perform operations on it, such as addition or deletion, since this property returns a list of nested cards.

## Property Management

To manage properties in cards and calendars, refer to this page:

{% content-ref url="property-management.md" %}
[property-management.md](property-management.md)
{% endcontent-ref %}

{% hint style="info" %}
You can create empty card instances using the `Card` class constructor, but you'll have to specify a version of vCard to be used, such as 2.1, 3.0, 4.0, or 5.0. The simplest way to create a card instance with no properties is:

```csharp
var card = new Card(new(2, 1));
```
{% endhint %}
