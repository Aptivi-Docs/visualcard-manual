---
description: Adding social media info to cards
icon: share-nodes
---

# Social Media URIs

Even though we have the URL property in cards, we needed to automatically generate social media URIs from cards that contain a specific property, called `X-VISUALCARD-SOCIAL`.

{% hint style="info" %}
You can use the [property management](../how-to-use/property-management.md) functions on cards and/or calendars to add, edit, remove, or fetch social media apps using `XNameInfo` as the type. Once done, you can use the `XNameInfo` instance to get the social media URI.
{% endhint %}

<details>

<summary>Compatible social media apps</summary>

Applications using VisualCard can process the following compatible social media apps to be displayed in the contact info box inside such applications:

<table><thead><tr><th width="130">App name</th><th width="245.3333740234375">Property value (abbreviation)</th><th>Property value (handle)</th></tr></thead><tbody><tr><td>Facebook</td><td><code>FB</code></td><td><code>username</code></td></tr><tr><td>X/Twitter</td><td><code>TW</code></td><td><code>username</code></td></tr><tr><td>Mastodon</td><td><code>MD</code></td><td><code>username@fedi.verse</code></td></tr><tr><td></td><td></td><td><code>fedi.verse;username@fedi.verse</code></td></tr><tr><td>Bluesky</td><td><code>BS</code></td><td><code>username@bsky.social</code></td></tr><tr><td>YouTube</td><td><code>YT</code></td><td><code>@username</code></td></tr><tr><td>Odysee</td><td><code>OD</code></td><td><code>@username</code></td></tr><tr><td>Instagram</td><td><code>IG</code></td><td><code>username</code></td></tr><tr><td>Snapchat</td><td><code>SC</code></td><td><code>username</code></td></tr><tr><td>TikTok</td><td><code>TK</code></td><td><code>@username</code></td></tr><tr><td>WhatsApp</td><td><code>WA</code></td><td><code>phoneNumber</code></td></tr><tr><td>Telegram</td><td><code>TG</code></td><td><code>username</code></td></tr></tbody></table>

{% hint style="info" %}
When generating URIs, the following is taken into account:

* Some social media apps, such as Facebook, X/Twitter, and Instagram, don't use the `@` (at) symbol for handles in the URIs.
* Some social media apps, such as YouTube, Odysee, and TikTok, use the `@` (at) symbol for handles in the URIs.
* You can optionally use the fediverse name, such as `fosstodon.org`, as the second argument directly after the `MD` type before the handle. If you omit the fediverse host name and just append your Mastodon handle, the fediverse host defaults to `mastodon.social`.
* So far, only WhatsApp uses the phone number to generate the URI.

You must use account handles in all cases. For example, if a person has a Mastodon account with the full name of "John Sanders", you'll have to get the handle, which is usually `jsanders@mastodon.social`.
{% endhint %}

</details>
