# Scan mich

*Scan Me — a lock screen business card*

Your business card as a QR code on your lock screen. Scannable without internet.

*Deutsch: Ein Hintergrundbild mit QR-Code für deinen Sperrbildschirm. Wer ihn scannt, hat dich im Adressbuch.*

---

## What it does

You type in your name and email — optionally phone, company, logo, job title and
website — and get a wallpaper sized for your phone, with a QR code in the free
zone of the lock screen. Someone points their camera at it and you land in their
contacts.

## Why it is different

**The contact data is inside the code, not behind a link.** Most QR business card
tools encode a URL that points at a hosted profile. That needs internet on the
scanning phone, and it stops working the day the service does. This one encodes a
**vCard 3.0** directly, so the scan works with no connection on either device — on
a plane, in a basement, at a conference with dead wifi.

**The placement is measured, not guessed.** The card sits in the area the lock
screen actually leaves free:

- **iOS 16+** — notifications grow *upward* from the bottom, so the middle stays
  clear. Measured free zone: 298 pt on a 393 × 852 pt screen.
- **Android** — notifications grow *downward* from the clock, so the layout is
  mirrored. Values taken from the AOSP SystemUI `dimens.xml`
  (`small_clock_height` 114 dp, `keyguard_clock_top_margin` 18 dp,
  `keyguard_indication_area_padding` 82 dp).

The device instructions come verbatim from the Apple and Google help pages, in
both languages — not translated, not invented.

## Privacy

Everything happens in your browser. Name, email, phone, company, logo — none of it
is sent anywhere, stored, or logged. The image is drawn on a `<canvas>` on your
device. Close the tab and it is gone.

The page itself counts visits with [GoatCounter](https://www.goatcounter.com) —
no cookies, no local storage, no IP addresses kept. That is the only external
request the page makes.

## Running it

Open `index.html`. That is all — no build step, no dependencies to install, no
server needed. The QR library
([qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator), ISC) is
inlined, the fonts are the system ones.

```
index.html         the tool, German and English
impressum.html     legal notice (German law)
datenschutz.html   privacy policy (German law)
```

Language follows, in order: `?lang=de` / `?lang=en` in the address, then your last
choice, then your browser setting.

## Design

Built in Figma first, then copied into code one to one — spacing, type scale,
colours and the two lock screen zone maps all live there.

## Licence

MIT — see [LICENSE](LICENSE).
