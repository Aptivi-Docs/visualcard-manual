---
description: Listing all the breaking changes.
icon: newspaper
---

# Breaking Changes

There are new releases of VisualCard that cause breaking changes, so you'll need to take them into consideration when upgrading your program to use later versions of VisualCard. Here are the version upgrade paths:

## VisualCard v0.x to v1.0

During the v0.x upgrade to v1.0, you'll need to consider the following:

### Main ALTID is now `-1`

The main ALTID number used to be `0`, because you could specify it or not in a property and the ALTID support was half-implemented. Now, because of the recent improvements to the parsing techniques that VisualCard uses, you can no longer implement some of the different property instances that have its ALTID value of `0`, such as `N` for name information. All main properties without their positive ALTID values will have their ALTID of `-1`, meaning that it's a main instance. For example, VisualCard will error out when seeing such properties implemented in a contact's vCard like this:

```
N:Navasquillo;Neville;Neville\,Nevile;Mr.;Jr.
N;ALTID=0;LANGUAGE=de:NAVASQUILLO;Neville;Neville\,Nevile;Mr.;Jr.
```

### Enforcing the correct types

In earlier versions of VisualCard, it allowed any and all of the types, even those that are not supported in all the RFC documents as specified in the [How to use](usage/how-to-use/) page. Starting from VisualCard v1.0, the following base types are supported:

* `HOME`, `WORK`, and `PREF`
* `X-nonstandard` types

The extra types are written in a separate page, [Card Parts](usage/how-to-use/card-parts.md).

If the type that is specified is not supported by a property, such as `warehouse` type in the address property, VisualCard will throw an exception. This will break cards that are generated in a non-standard way.
