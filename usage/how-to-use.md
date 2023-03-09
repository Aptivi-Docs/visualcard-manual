---
description: How do you use it?
---

# 🖥 How to use

Using this library is very simple! Just use the `VisualCard` namespace in any piece of code you want to use the library, as in: `using VisualCard;`

Just use the `CardTools` class that contains:

* `GetCardParsersFromString(string)`
* `GetCardParsers(string)`
* `GetCardParsers(StreamReader)`

These functions return the list of card parsers in case multiple contacts are spotted. This is useful to parse each individual contact with `Parse()` in each individual `BaseVcardParser` instance for said contact.

`Parse()` must be called on the individual parser to return a `Card` instance that holds information about the contact, including:

| Key           | VCard 2.1 | VCard 3.0 | VCard 4.0 |
| ------------- | --------- | --------- | --------- |
| `KIND`        |           |           | ●         |
| `N`           | ●         | ●         | ●         |
| `FN`          | ●         | ●         | ●         |
| `TEL`         | ●         | ●         | ●         |
| `ADR`         | ●         | ●         | ●         |
| `EMAIL`       | ●         | ●         | ●         |
| `ORG`         | ●         | ●         | ●         |
| `TITLE`       | ●         | ●         | ●         |
| `URL`         | ●         | ●         | ●         |
| `NOTE`        | ●         | ●         | ●         |
| `PHOTO`       | ●         | ●         | ●         |
| `LOGO`        | ●         | ●         | ●         |
| `SOUND`       | ●         | ●         | ●         |
| `REV`         | ●         | ●         | ●         |
| `NICKNAME`    |           | ●         | ●         |
| `BDAY`        | ●         | ●         | ●         |
| `MAILER`      | ●         | ●         |           |
| `ROLE`        | ●         | ●         | ●         |
| `CATEGORIES`  |           | ●         | ●         |
| `PRODID`      |           | ●         | ●         |
| `SORT-STRING` |           | ●         | ●         |
| `TZ`          | ●         | ●         | ●         |
| `GEO`         | ●         | ●         | ●         |
| `X-NAME`      | ●         | ●         | ●         |

To save contacts, call the `Save()` function on a `Card` instance that holds information about a contact you want to save.

{% hint style="info" %}
On VCard 4.0, ALTID is supported on all the compatible types.
{% endhint %}
