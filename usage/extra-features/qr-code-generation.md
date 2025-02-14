---
description: Generating QR code for your contacts or your calendars?
icon: qrcode
---

# QR Code Generation

If you want to generate QR code for your contacts or your calendars, you can use one of the `VisualCard.Extras` features to facilitate this task. The class required to generate QR codes, `QrCodeGenerator`, allows you to perform the following operations:

* `SaveQrCode()`: Saves the QR code of a card instance, a calendar instance, or a MeCard string representation to a byte array representing the PNG image.
* `ExportQrCode()`: Exports the QR code of a card instance, a calendar instance, or a MeCard string representation to a `.qrr` file containing QR code data that can be used by any other application using [`QrCoder`](https://github.com/codebude/QRCoder).
