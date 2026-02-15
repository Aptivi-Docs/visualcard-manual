---
description: Generating QR code for your contacts or your calendars?
icon: qrcode
---

# QR Code Generation

If you want to generate QR code for your contacts or your calendars, you can use one of the `VisualCard.Extras` features to facilitate this task.

***

## <mark style="color:$primary;">QR code generator class</mark>

The class required to generate QR codes, `QrCodeGenerator`, allows you to perform the following operations:

<table><thead><tr><th width="149.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>SaveQrCode()</code></td><td>Saves the QR code of a card instance, a calendar instance, or a MeCard string representation to a byte array representing the PNG image.</td></tr><tr><td><code>ExportQrCode()</code></td><td>Exports the QR code of a card instance, a calendar instance, or a MeCard string representation to a <code>.qrr</code> file containing QR code data that can be used by any other application using <a href="https://github.com/codebude/QRCoder"><code>QrCoder</code></a>.</td></tr></tbody></table>
