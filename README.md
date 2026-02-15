---
description: Welcome to VisualCard!
icon: hand-wave
---

# Welcome!

VisualCard is a library that parses the VCard Files (`.vcf`), whether it's a single contact or a multiple contact file. It's compatible with both .NET Framework 4.8 and the modern .NET runtime.

## <mark style="color:$primary;">Release history</mark>

Below is the release history of the library:

{% updates format="full" %}
{% update date="2025-12-01" %}
## <mark style="color:$primary;">v4.1.2.2</mark>

<mark style="color:yellow;">Fixed logging always writing to log files even if logging is disabled</mark>
{% endupdate %}

{% update date="2025-11-23" %}
## <mark style="color:$primary;">v4.1.2.1</mark>

<mark style="color:yellow;">Fixed agent comparison always returning false</mark>
{% endupdate %}

{% update date="2025-10-27" %}
## <mark style="color:$primary;">v4.1.2</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2025-10-25" %}
## <mark style="color:$primary;">v4.1.1</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2025-07-03" %}
## <mark style="color:$primary;">v4.1.0</mark>

<mark style="color:green;">Added localized strings</mark>
{% endupdate %}

{% update date="2025-04-30" %}
## <mark style="color:$primary;">v4.0.0.3</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2025-04-23" %}
## <mark style="color:$primary;">v4.0.0.2</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2025-02-21" %}
## <mark style="color:$primary;">v4.0.0.1</mark>

<mark style="color:yellow;">General improvements and bug fixes</mark>
{% endupdate %}

{% update date="2025-02-16" %}
## <mark style="color:$primary;">v4.0.0</mark>

<mark style="color:green;">You can now add, edit, and delete properties and components!</mark>

<mark style="color:green;">Added social media URI generation</mark>

<mark style="color:green;">Introducing</mark> <mark style="color:green;"></mark><mark style="color:green;">`VisualCard.Common`</mark> <mark style="color:green;"></mark><mark style="color:green;">that contains versit-agnostic tools</mark>

<mark style="color:green;">Added logging support</mark>

<mark style="color:yellow;">IANA and X-nonstandard properties are no longer versit-specific</mark>

<mark style="color:yellow;">Refactored the codebase</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2025-01-16" %}
## <mark style="color:$primary;">v3.3.0</mark>

<mark style="color:green;">Added QUOTED-PRINTABLE support for cards and calendars</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2024-11-09" %}
## <mark style="color:$primary;">v3.2.0</mark>

<mark style="color:yellow;">Merged CalendarValueInfo and CardValueInfo</mark>

<mark style="color:yellow;">ValueInfo equality comparison now also compares the values</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2024-10-12" %}
## <mark style="color:$primary;">v3.1.2</mark>

<mark style="color:yellow;">Updated Textify</mark>
{% endupdate %}

{% update date="2024-10-10" %}
## <mark style="color:$primary;">v3.1.1</mark>

<mark style="color:yellow;">Updated libraries</mark>
{% endupdate %}

{% update date="2024-10-09" %}
## <mark style="color:$primary;">v3.1.0</mark>

<mark style="color:green;">Added</mark> <mark style="color:green;"></mark><mark style="color:green;">`PropertyInfo`</mark>

<mark style="color:green;">Added part dictionary properties (strings, integers, and parts array instances)</mark>

<mark style="color:green;">Added support for nested property groups</mark>

<mark style="color:yellow;">Better support for whitespace padded properties and their arguments</mark>

<mark style="color:yellow;">General improvements and bug fixes</mark>
{% endupdate %}

{% update date="2024-10-03" %}
## <mark style="color:$primary;">v3.0.0</mark>

<mark style="color:green;">Added more vCard and vCalendar properties (100% of them!)</mark>

<mark style="color:green;">Added recurrence parser</mark>

<mark style="color:green;">Added duration, date/time, and UTC offset parsers</mark>

<mark style="color:green;">Added property grouping support</mark>

<mark style="color:green;">Added value info, property info, and argument info instances</mark>

<mark style="color:green;">Added support for more than one string and integer</mark>

<mark style="color:yellow;">Moved extra tools to VisualCard.Extras</mark>

<mark style="color:yellow;">Massive improvements to vCard and vCalendar parsers</mark>

<mark style="color:yellow;">Property names are now case-insensitive</mark>

<mark style="color:yellow;">Mass migrated several text-based arrays to strings</mark>

<mark style="color:yellow;">General improvements and bug fixes</mark>
{% endupdate %}

{% update date="2024-09-23" %}
## <mark style="color:$primary;">v2.3.0</mark>

<mark style="color:green;">Added more calendar properties</mark>

<mark style="color:green;">Added type support for calendars</mark>
{% endupdate %}

{% update date="2024-09-23" %}
## <mark style="color:$primary;">v2.2.0</mark>

<mark style="color:yellow;">Improved time zone offset support</mark>
{% endupdate %}

{% update date="2024-09-11" %}
## <mark style="color:$primary;">v2.1.0</mark>

<mark style="color:green;">Added a lot of vCalendar properties</mark>

<mark style="color:green;">Added all calendar components</mark>

<mark style="color:green;">Added full nullable support</mark>

<mark style="color:green;">Added full calendar saving</mark>

<mark style="color:green;">Added calendar component comparison</mark>

<mark style="color:yellow;">Improved calendar event and component querying</mark>

<mark style="color:yellow;">Improved validation code</mark>

<mark style="color:yellow;">General improvements and bug fixes</mark>
{% endupdate %}

{% update date="2024-09-03" %}
## <mark style="color:$primary;">v2.0.0</mark>

<mark style="color:green;">Added very basic vCalendar implementation</mark>

<mark style="color:green;">Added nested cards support</mark>

<mark style="color:green;">Added UID support</mark>

<mark style="color:yellow;">Improved newline handling</mark>

<mark style="color:yellow;">General improvements and bug fixes</mark>
{% endupdate %}

{% update date="2024-08-13" %}
## <mark style="color:$primary;">v1.1.1</mark>

<mark style="color:yellow;">Updated libraries</mark>
{% endupdate %}

{% update date="2024-07-02" %}
## <mark style="color:$primary;">v1.1.0</mark>

<mark style="color:green;">Added getting blob stream from keys, images, sounds, and logos</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2024-06-22" %}
## <mark style="color:$primary;">v1.0.1</mark>

<mark style="color:yellow;">Updated libraries</mark>
{% endupdate %}

{% update date="2024-04-04" %}
## <mark style="color:$primary;">v1.0.0.1</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2024-04-04" %}
## <mark style="color:$primary;">v1.0.0</mark>

<mark style="color:green;">Added new types</mark>

<mark style="color:green;">Added global line folding</mark>

<mark style="color:green;">Added a dictionary representing values</mark>

<mark style="color:green;">Added videophone and phonetics to MeCard</mark>

<mark style="color:green;">Added vCard to MeCard conversion</mark>

<mark style="color:green;">Added card generator</mark>

<mark style="color:yellow;">Overhauled the parser!</mark>

<mark style="color:yellow;">Enforced ALTID and types</mark>

<mark style="color:yellow;">Enforced cardinality</mark>

<mark style="color:yellow;">Fixed bugs and issues</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2024-02-14" %}
## <mark style="color:$primary;">v0.9.3</mark>

<mark style="color:yellow;">Updated libraries</mark>
{% endupdate %}

{% update date="2024-02-06" %}
## <mark style="color:$primary;">v0.9.2</mark>

<mark style="color:yellow;">Changed symbol nupkg to snupkg</mark>
{% endupdate %}

{% update date="2023-12-21" %}
## <mark style="color:$primary;">v0.9.1</mark>

<mark style="color:yellow;">Facilitated debugging by using Source Link</mark>
{% endupdate %}

{% update date="2023-12-16" %}
## <mark style="color:$primary;">v0.9.0</mark>

<mark style="color:green;">Added support for vCard 5.0 contacts</mark>

<mark style="color:green;">Added AGENT for v2.1, 3.0, and 5.0 vCard contacts</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2023-11-25" %}
## <mark style="color:$primary;">v0.8.4</mark>

<mark style="color:yellow;">Improved MeCard conversion</mark>
{% endupdate %}

{% update date="2023-11-14" %}
## <mark style="color:$primary;">v0.8.3</mark>

<mark style="color:yellow;">Updated all libraries</mark>
{% endupdate %}

{% update date="2023-10-25" %}
## <mark style="color:$primary;">v0.8.2</mark>

<mark style="color:yellow;">Upgraded the SQLite library for Android contacts support</mark>
{% endupdate %}

{% update date="2023-10-11" %}
## <mark style="color:$primary;">v0.8.1</mark>

<mark style="color:yellow;">Updated the SQLite support library to 7.0.12</mark>
{% endupdate %}

{% update date="2023-10-01" %}
## <mark style="color:$primary;">v0.8.0</mark>

<mark style="color:green;">Added LABEL and CLASS properties</mark>

<mark style="color:green;">Added support for relation, contact event, and identifier to the Android parser</mark>

<mark style="color:yellow;">Fixed photo, logo, and sound parsing causing crashes</mark>
{% endupdate %}

{% update date="2023-09-18" %}
## <mark style="color:$primary;">v0.7.1</mark>

<mark style="color:yellow;">Fixed crash when parsing some generated VCards</mark>
{% endupdate %}

{% update date="2023-09-18" %}
## <mark style="color:$primary;">v0.7.0</mark>

<mark style="color:green;">Added signing (strong name)</mark>

<mark style="color:green;">Added documentation</mark>
{% endupdate %}

{% update date="2023-09-13" %}
## <mark style="color:$primary;">v0.5.1</mark>

<mark style="color:yellow;">Signed with the Aptivi signing key</mark>
{% endupdate %}

{% update date="2023-08-12" %}
## <mark style="color:$primary;">v0.6.0.0</mark>

<mark style="color:green;">Added MeCard parsing support</mark>

<mark style="color:yellow;">Improved the VCard parsers</mark>
{% endupdate %}

{% update date="2023-08-10" %}
## <mark style="color:$primary;">v0.5.0.0</mark>

<mark style="color:green;">Added support for 5 new variables</mark>

<mark style="color:yellow;">Improved the card parsing functionality</mark>
{% endupdate %}

{% update date="2023-04-01" %}
## <mark style="color:$primary;">v0.4.0.0</mark>

<mark style="color:yellow;">First block of image, sound, or logo should align exactly to 74 characters</mark>

<mark style="color:yellow;">Reworked on type and argument value getters</mark>

<mark style="color:yellow;">Fixed crashes related to argument parsing</mark>
{% endupdate %}

{% update date="2023-03-28" %}
## <mark style="color:$primary;">v0.3.0.0</mark>

<mark style="color:green;">Added saving cards to string</mark>

<mark style="color:green;">Added limited support for Android contacts database support</mark>

<mark style="color:green;">Added equality for cards</mark>

<mark style="color:green;">Added organization type</mark>

<mark style="color:yellow;">Improved argument parsing for VCard 4.0</mark>

<mark style="color:yellow;">Added AltArguments to the rest of the info classes</mark>

<mark style="color:yellow;">Improved VCard generation for Alt ID</mark>

<mark style="color:yellow;">General improvements</mark>
{% endupdate %}

{% update date="2023-03-02" %}
## <mark style="color:$primary;">v0.2.0.0</mark>

<mark style="color:green;">Added VCard parsing by file, by stream, or by string</mark>

<mark style="color:yellow;">Fixed grammatical error on parse errors</mark>

<mark style="color:yellow;">Fixed titles not being parsed</mark>

<mark style="color:yellow;">Improved saving</mark>
{% endupdate %}

{% update date="2023-02-20" %}
## <mark style="color:$primary;">v0.1.0.0</mark>

<mark style="color:green;">Added support for new card values (Timezone, geography, etc.)</mark>

<mark style="color:yellow;">Fixed parsing with separate contacts delimited by newlines</mark>

<mark style="color:yellow;">Extended ALTID support to more types</mark>
{% endupdate %}

{% update date="2023-02-17" %}
## <mark style="color:$primary;">v0.1.0.0-alpha04</mark>

<mark style="color:yellow;">Re-targeted to .NET Standard 2.0</mark>

<mark style="color:yellow;">Fixed VCard and photo parsing</mark>

<mark style="color:yellow;">Fixed stuck file handle</mark>
{% endupdate %}

{% update date="2022-08-18" %}
## <mark style="color:$primary;">v0.1.0.0-alpha03</mark>

<mark style="color:green;">Added more types (BDAY, REV, ...)</mark>

<mark style="color:yellow;">Improved ALTID parsing</mark>
{% endupdate %}

{% update date="2022-08-17" %}
## <mark style="color:$primary;">v0.1.0.0-alpha02</mark>

<mark style="color:green;">Added photo</mark>

<mark style="color:yellow;">Reduced NuGet download size</mark>
{% endupdate %}

{% update date="2022-06-27" %}
## <mark style="color:$primary;">v0.1.0.0-alpha01</mark>

The initial release of the library is now live!
{% endupdate %}
{% endupdates %}
