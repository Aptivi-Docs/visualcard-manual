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

<table><thead><tr><th width="163.8193359375">Key</th><th width="103.41119384765625">VCard 2.1</th><th width="110">VCard 3.0</th><th>VCard 4.0</th></tr></thead><tbody><tr><td><code>KIND</code></td><td></td><td></td><td>●</td></tr><tr><td><code>N</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>FN</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TEL</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ADR</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>EMAIL</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>ORG</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>TITLE</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>URL</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NOTE</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>PHOTO</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>LOGO</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOUND</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>REV</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>NICKNAME</code></td><td></td><td>●</td><td>●</td></tr><tr><td><code>BDAY</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>MAILER</code></td><td>●</td><td>●</td><td></td></tr><tr><td><code>ROLE</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>CATEGORIES</code></td><td></td><td>●</td><td>●</td></tr><tr><td><code>PRODID</code></td><td></td><td>●</td><td>●</td></tr><tr><td><code>SORT-STRING</code></td><td></td><td>●</td><td>●</td></tr><tr><td><code>TZ</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>GEO</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>IMPP</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>SOURCE</code></td><td>●</td><td>●</td><td>●</td></tr><tr><td><code>XML</code></td><td></td><td></td><td>●</td></tr><tr><td><code>FBURL</code></td><td></td><td></td><td>●</td></tr><tr><td><code>CALURI</code></td><td></td><td></td><td>●</td></tr><tr><td><code>CALADRURI</code></td><td></td><td></td><td>●</td></tr><tr><td><code>X-NAME</code></td><td>●</td><td>●</td><td>●</td></tr></tbody></table>

To save contacts, call the `Save()` function on a `Card` instance that holds information about a contact you want to save.

{% hint style="info" %}
On VCard 4.0, `ALTID` is supported on all the compatible types.
{% endhint %}

### Conversion from different contacts

VisualCard not only parses the standard VCard contacts, but it also supports conversion from different contact formats to their VCard 3.0 counterparts by parsing these formats and forming a VCard 3.0 representation to be parsed by VisualCard. The below supported types are as follows:

* Android `contacts2.db` from the contacts provider
* MeCard string used to generate QR codes

#### Android `contacts2.db`

Using the `contacts2.db` file found in the contact provider's data files found under `/data/data/android.providers.contacts/databases`, you can convert this file to be parsable by VisualCard's VCard 3.0 parser.

You can invoke `GetContactsFromDb()` from the `AndroidContactsDb` class, provided that you provide a path to this file on your local computer's drive.

{% hint style="warning" %}
In the first glance, this sounds easy. However, you need to know how to obtain the `contacts2.db` file from the contacts provider, which is only possible by rooting your Android device.

If your ROM provides ADB root shell, like LineageOS and the like, you can connect your phone to your computer and install [platform-tools](https://developer.android.com/tools/releases/platform-tools) to install ADB.

If the file is not there in the above path, you may need to look for this file name under the user's data folder, such as `/data/user/0/com.android.providers.contacts/databases/contacts2.db` for most devices.

Furthermore, some stock ROMs, like Motorola, might store their contacts in `/data/user/0/com.motorola.blur.providers.contacts/databases/contacts2.db` instead.

After installing ADB to your PATH, run the following commands:

```shell-session
$ adb root
$ adb pull /data/data/android.providers.contacts/databases/contacts2.db path/to/contacts2.db
```
{% endhint %}

{% hint style="danger" %}
**Be cautious, because rooting will cause your warranty to be void. Latest devices also need to have their bootloader (a program responsible for starting Android) unlocked (OEM unlocking) before rooting process succeeds.**

_**Unlocking the bootloader may cause your user data to be wiped.**_

_**In some cases, your device might fail to boot to Android if done incorrectly.**_
{% endhint %}

`GetContactsFromDb()` returns a list of base VCard parsers that can be parsed by calling the `Parse()` function on them. Usually, you can just enumerate through all the base parsers to get contact information about all of them.

Below is an example of how to extract VCard parsers and parse them from Android's `contacts2.db`:

```csharp
List<Card> Contacts = new();
List<BaseVcardParser> ContactParsers = AndroidContactsDb.GetContactsFromDb(args[0]);
foreach (BaseVcardParser ContactParser in ContactParsers)
{
    Card Contact = ContactParser.Parse();
    Contacts.Add(Contact);
}
```

Below are the supported contact elements for the conversion (found under the `vnd.android.cursor.item` group):

| Android             | VCard 3.0                                   |
| ------------------- | ------------------------------------------- |
| `name`              | <p><code>N</code></p><p><code>FN</code></p> |
| `phone_v2`          | `TEL`                                       |
| `nickname`          | `NICKNAME`                                  |
| `email_v2`          | `EMAIL`                                     |
| `postal-address_v2` | `ADR`                                       |
| `im`                | `X-[AOL\|MSN\|QQ\|...]`                     |
| `organization`      | `ORG`                                       |
| `website`           | `URL`                                       |
| `sip_address`       | `IMPP`                                      |
| `note`              | `NOTE`                                      |
| `photo`             | `PHOTO`                                     |

#### MeCard strings

MeCard is commonly used for scannable contacts, usually generated by the QR code generators. This is typically used so that smartphone owners can easily scan the contact's QR code to add the contact to the phone. This is faster than a person manually typing their phone number and their details on a pen and a paper.

In order to parse MeCard strings, you'll have to use the `GetContactsFromMeCardString()` function found in the `MeCard` class. Like the above converter, you'll have to manually call `Parse()` on each base VCard parser so that you can get contact information on a VCard class.

This converter supports about anything a MeCard contact can have. Here are the supported types:

| MeCard     | VCard 3.0  |
| ---------- | ---------- |
| `ADR`      | `ADR`      |
| `BDAY`     | `BDAY`     |
| `EMAIL`    | `EMAIL`    |
| `N`        | `N`        |
| `NICKNAME` | `NICKNAME` |
| `NOTE`     | `NOTE`     |
| `TEL`      | `TEL`      |
| `URL`      | `URL`      |

{% hint style="info" %}
This converter can't convert `TEL-AV` and `SOUND` types. `SOUND` on MeCard was defined as:

_Designates a text string to be set as the kana name in the phonebook._
{% endhint %}
