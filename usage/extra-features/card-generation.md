---
icon: address-card
description: Generating your cards automagically...
---

# Card Generation

In addition to VisualCard having the most basic card parsing functions, you can now generate cards based on a random name generation function employed by the Textify library that you can consult here:

{% content-ref url="https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/NaUWjRlaBR1k5rO42Zy8/" %}
[Textify - Manual](https://app.gitbook.com/o/fj052nYlsxW9IdL3bsZj/s/NaUWjRlaBR1k5rO42Zy8/)
{% endcontent-ref %}

You can generate cards using the following two function overloads:

* `GenerateCards()`: generates up to 100 cards by default (you can override this using the optional parameters)
* `GenerateCards(int cards)`: generates exactly a number of specified cards

It uses the list of first and the last names to generate random names. It occasionally adds one or both of telephone and e-mail information for one of home, work, or both. Once done, the generator lets VisualCard parse the generated card instance to verify that it's been generated correctly.
