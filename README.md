# 🔐 AuthBridge

### Move your 2FA accounts. Keep your secrets private.

A free, open-source Google Authenticator migration tool that runs entirely in your browser.

**[Launch AuthBridge](https://kja6x.github.io/authbridge/)**

Scan your Google Authenticator export QR codes, then generate individual QR codes compatible with other authenticator apps. **No registration or backend uploads.**

---

## About AuthBridge

AuthBridge is a free, open-source, browser-based tool for transferring Google Authenticator accounts to other authenticator apps that support standard `otpauth://` QR codes.

## What it does

- Scan a Google Authenticator export QR code with your camera.
- Import QR screenshots or images.
- Paste `otpauth-migration://` or individual `otpauth://` links.
- Decode multiple accounts and multi-part Google Authenticator exports.
- Generate individual, standard authenticator QR codes for importing elsewhere.
- Copy `otpauth://` URIs, secrets, or current TOTP codes.
- Export account details as JSON (**contains sensitive secrets**).

## Try it

Visit **https://kja6x.github.io/authbridge/**

## How to migrate

1. In Google Authenticator, open **Transfer accounts / Export accounts** (wording varies by version).
2. Display the export QR code(s).
3. Open AuthBridge on another device and scan each QR code, or import screenshots where appropriate.
4. For each imported account, select **Show authenticator QR**.
5. Scan that individual QR code using your destination authenticator app.
6. **Verify the new app's code works on the corresponding service before removing the original account.**

> [!NOTE]
> Apps may differ in their support for HOTP, SHA-256, SHA-512, and eight-digit codes. Standard six-digit SHA-1 TOTP is the most broadly compatible.

## Privacy and security

QR images and account secrets are processed in your browser; this application **does not upload them to a backend**. However, the current HTML loads third-party JavaScript from CDNs.

> [!WARNING]
> Migration QR codes, secret keys, generated QR codes, and exported JSON are equivalent to credentials. **Never post screenshots or exports publicly.** Avoid browser extensions that can read page contents. This tool does not replace your existing authenticator or store a recoverable backup.

## Development

The project is currently a single static HTML page with browser-side JavaScript. No database or application server is required.

To run it locally, choose either Python or Node.js. Run the command from the repository directory.

**Python:**

```bash
python3 -m http.server 8000
```

**Node.js (no global installation required):**

```bash
npx http-server . -p 8000 -c-1
```

Alternatively, with the `serve` package:

```bash
npx serve . -l 8000
```

Then visit **http://localhost:8000**. The `http-server` option `-c-1` disables caching during development. `npx` may prompt to download the selected package on first use.

## Contributing

Bug reports, security reviews, compatibility tests, accessibility improvements, and translations are welcome.

**Do not attach real QR codes, authenticator secrets, or JSON exports to issues.** Use synthetic test credentials.

## Disclaimer

Independent community project. Not affiliated with or endorsed by Google or any authenticator vendor. Always test transferred accounts before deleting their original entries.

## License

MIT License. Third-party JavaScript dependencies retain their respective licenses.
