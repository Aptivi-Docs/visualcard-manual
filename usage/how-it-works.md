---
description: How does it work?
---

# ⚒ How it works

VisualCard parses the contact files in two stages:

## Stage 1: Card Parsers

When either a string containing a path to the VCard file (`GetCardParsers(string)`) or a string containing the VCard content (`GetCardParsersFromString(string)`) or a stream containing the VCard content (`GetCardParsers(StreamReader)`) is passed, VisualCard converts the content to a stream first in case we encounter the large VCard file.

VisualCard then attempts to parse all the lines line by line, but first looks for the VCard header at exactly the first line:

```vcard
BEGIN:VCARD
```

Each contact file must begin with the above header, and each contact in a single file must have the begin and the end tags. Parsing fails if omitted.

After the begin tag is spotted, it looks for the version in the exact second line of each contact. If it's either one of:

* `VERSION:2.1`
* `VERSION:3.0`
* `VERSION:4.0`

VisualCard will append the card version to the `CardVersion` property of the parser. VisualCard will then keep adding lines of content until the ending tag is spotted, `END:VCARD`.

Once the ending tag is seen, VisualCard will select the best VCard parser based on the below versions:

* `VERSION:2.1` -> `VcardTwo`
* `VERSION:3.0` -> `VcardThree`
* `VERSION:4.0` -> `VcardFour`

VisualCard will then create a new instance of the selected inherited `BaseVcardParser` class containing necessary functions to parse the contact.

## Stage 2: Actual parsing

Upon calling `Parse()` on the individual contact parser instance, VisualCard's parser will attempt to process all the keys found in the card content, `CardContent`.

`Parse()` first checks to see if the card content is sane, as in:

* ...the version of the VCard contact found within the `CardContent` matches the version which the parser expects
* ...the card content is not empty

Once these checks were made, the parser processes each key found. In VCard 4.0, VisualCard will take the ALTID for each supported key with their own cardinality into account.

Once the parser finishes installing all the values from all the supported keys, VisualCard checks for the below requirements:

| VCard     | `N` | `FN` |
| --------- | --- | ---- |
| VCard 2.1 | ●   |      |
| VCard 3.0 | ●   | ●    |
| VCard 4.0 |     | ●    |

If the requirements are met, VisualCard returns a new `Card` instance that you can fetch its values from.

## Spec sheets

Each VCard version comes with its own data specification sheets as defined as Request For Comments (RFCs) defined by the Internet Engineering Task Force (IETF):

* [VCard 2.1](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-21.txt)
* [VCard 3.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-30-rfc2426.txt)
* [VCard 4.0](https://github.com/Aptivi/VisualCard/raw/main/VisualCard/Specs/vcard-40-rfc6350.txt)
