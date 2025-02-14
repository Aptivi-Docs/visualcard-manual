---
description: Adding social media info to cards
icon: share-nodes
---

# Social Media URIs

Even though we have the URL property in cards, we needed to automatically generate social media URIs from cards that contain a specific property, called `X-VISUALCARD-SOCIAL`. This is so that applications using VisualCard can process the following compatible social media apps to be displayed in the contact info box inside such applications: (the abbreviations must be in the first value of this property)

* Facebook (`FB`)
* X/Twitter (`TW`)
* Mastodon (`MD`)
* Bluesky (`BS`)
* YouTube (`YT`)
* Odysee (`OD`)
* Instagram (`IG`)
* Snapchat (`SC`)
* TikTok (`TK`)
* WhatsApp (`WA`)
* Telegram (`TG`)

{% hint style="info" %}
When generating URIs, the following is taken into account:

* Some social media apps, such as Facebook, X/Twitter, and Instagram, don't use the `@` (at) symbol for handles in the URIs.
* Some social media apps, such as YouTube, Odysee, and TikTok, use the `@` (at) symbol for handles in the URIs.
* You can optionally use the fediverse name, such as `fosstodon.org`, as the second argument directly after the `MD` type before the handle. If you omit the fediverse host name and just append your Mastodon handle, the fediverse host defaults to `mastodon.social`.
* So far, only WhatsApp uses the phone number to generate the URI.

You must use account handles in all cases. For example, if a person has a Mastodon account with the full name of "John Sanders", you'll have to get the handle, which is usually `jsanders@mastodon.social`.
{% endhint %}

You can use the [property management](../how-to-use/property-management.md) functions on cards and/or calendars to add, edit, remove, or fetch social media apps using `XNameInfo` as the type. Once done, you can use the `XNameInfo` instance to get the social media URI.
