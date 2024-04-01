---
description: How does it work?
---

# ⚒️ How it works

When either a string containing a path to the VCard file (`GetCards(string)`) or a string containing the VCard content (`GetCardsFromString(string)`) or a stream containing the VCard content (`GetCards(StreamReader)`) is passed, VisualCard converts the content to a stream first in case we encounter the large VCard file.

VisualCard then attempts to parse all the lines line by line, but first looks for the VCard header at exactly the first line:

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

The parser first checks to see if the card content is not empty to verify that the builder works right. Once these checks were made, the parser processes each key found. In VCard 4.0 and 5.0, VisualCard takess the ALTID for each supported key with their own cardinality into account.

Once the parser finishes installing all the values from all the supported keys, VisualCard checks for the below requirements:

| VCard     | Name (N) | Full name (FN) |
| --------- | -------- | -------------- |
| vCard 2.1 | ●        |                |
| vCard 3.0 | ●        | ●              |
| vCard 4.0 |          | ●              |
| vCard 5.0 |          |                |

If the requirements are met, VisualCard returns a new `Card` instance that you can fetch its values from using one of the following methods:

* `GetPartsArray()`
* `GetPart()`
* `GetString()`

## Spec sheets

Each vCard version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF), except that VisualCard also supports vCard 5.0, which is defined by Aptivi:

* [vCard 2.1](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-21.txt)
* [vCard 3.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-30-rfc2426.txt)
* [vCard 4.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-40-rfc6350.txt)
* [vCard 5.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-50-aptivi.txt)
