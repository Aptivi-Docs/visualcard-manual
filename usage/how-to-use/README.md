---
description: How do you use it?
---

# 🖥️ How to use

Using this library is very simple! Just use the `VisualCard` namespace in any piece of code you want to use the library, as in: `using VisualCard;`

Just use the `CardTools` class that contains:

* `GetCardsFromString(string)`
* `GetCards(string)`
* `GetCards(StreamReader)`

These functions return the list of cards from multiple contacts that may be detected by the vCard parser. When parsing is done, it returns an array of `Card` instances that hold information about the contact. You can consult the supported parts in the below page:

{% content-ref url="card-parts.md" %}
[card-parts.md](card-parts.md)
{% endcontent-ref %}

{% hint style="info" %}
VisualCard officially supports the vCard 5.0 specification, which can be found [here](https://github.com/Aptivi/VisualCard/blob/main/VisualCard/Specs/vcard-50-aptivi.txt).
{% endhint %}

To save contacts, call the `SaveTo()` function on a `Card` instance that holds information about a contact you want to save. Currently, it allows you to specify the method of saving:

* `SaveTo()`: Saves this contact to a file path
* `SaveToString()`: Saves this contact to a string representation

{% hint style="info" %}
On VCard 4.0 and 5.0, `ALTID` is supported on all the compatible types.
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

If your ROM provides ADB root shell, like [LineageOS](https://lineageos.org/) and the like, you can connect your phone to your computer and install [platform-tools](https://developer.android.com/tools/releases/platform-tools) to install ADB.

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

`GetContactsFromDb()` returns a list of parsed vCard card instance classes. Below is an example of how to parse vCard contacts from Android's `contacts2.db`:

```csharp
// If you already have contacts2.db somewhere in your computer
Card[] contactsSpecific = AndroidContactsDb.GetContactsFromDb(args[0]);

// If you're running rooted Android and you need to parse from the system path
Card[] contactsSystem = AndroidContactsDb.GetContactsFromDb();
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

{% hint style="danger" %}
Unless you implement some kind of root checker in your application and have a reason to parse contacts the root way, we advice you to use built-in Android functions within your code using [ContactsContract.Contacts](https://learn.microsoft.com/en-us/dotnet/api/android.provider.contactscontract.contacts).
{% endhint %}

#### MeCard strings

MeCard is commonly used for scannable contacts, usually generated by the QR code generators. This is typically used so that smartphone owners can easily scan the contact's QR code to add the contact to the phone. This is faster than a person manually typing their phone number and their details on a pen and a paper.

In order to parse MeCard strings, you'll have to use the `GetContactsFromMeCardString()` function found in the `MeCard` class. Like the above converter, you can get contact information on a vCard class instantly.

This converter supports about anything a MeCard contact can have. Here are the supported types:

| MeCard     | VCard 3.0           |
| ---------- | ------------------- |
| `ADR`      | `ADR`               |
| `BDAY`     | `BDAY`              |
| `EMAIL`    | `EMAIL`             |
| `N`        | `N`                 |
| `NICKNAME` | `NICKNAME`          |
| `NOTE`     | `NOTE`              |
| `SOUND`    | `X-VISUALCARD-KANA` |
| `TEL`      | `TEL`               |
| `TEL-AV`   | `TEL;TYPE=VIDEO`    |
| `URL`      | `URL`               |

{% hint style="info" %}
`SOUND` on MeCard is defined in Japanese phonebooks as:

_Designates a text string to be set as the kana name in the phonebook._

As there is no native equivalent of **Kana Name** in any of the vCard specifications, such as `KANA:[...]`, you can access this value after the conversion using the `X-VISUALCARD-KANA` property.
{% endhint %}
