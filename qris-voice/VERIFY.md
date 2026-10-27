# Infinity QRIS Voice — Verification & Trust

This page is the public verification record for **Infinity QRIS Voice** distributed by Infinity Digital.

## Official identity

- Android package: `com.infinity.qrisvoice`
- Official website: https://infinityai.id/qris-voice/
- Official Telegram bot: https://t.me/infinitydigitalstorebot
- Official community invite: https://t.me/+W6H55z8tjwY0Njc1
- Release signer: `CN=Infinity AI, OU=Infinity Team, O=Infinity Digital, L=Jakarta, ST=DKI, C=ID`
- Signing certificate SHA-256:
  `19a021c195943d5b82bf466aa7e4a5c02c4bbf72a9070eba87e9a1c6a3d9b0d4`

The **signing certificate fingerprint is the primary identity check** for APK updates. A file with a different signing certificate must not be treated as an official Infinity QRIS Voice update.

## Current release candidate

The current signed release candidate is:
- [1.0.1-beta / build 3 release record](releases/1.0.1-beta-build3.json)

Previous public binary record:
- [1.0.0-beta / build 2](releases/1.0.0-beta-build2.json)

Build 3 becomes the public website release only after the website, Telegram gate, version manifest, and download controls are verified live.

## What the app needs

Infinity QRIS Voice is a native Android utility because it uses Android's Notification Listener service to detect incoming payment notifications from a payment app selected by the user.

The app is designed so that:

- payment detection and voice announcement do not depend on an Infinity payment-processing server;
- transaction history is stored locally on the Android device;
- Smart Learn / calibration observations are temporary and local to the device;
- SMS, contacts and location are not required for the payment-listener workflow;
- the app does not require a bank PIN, OTP, password or internet-banking credential;
- Notification Access can be revoked by the user at any time.

On Xiaomi / Redmi / POCO / HyperOS devices, **Auto-start / Mulai Otomatis** may be required so Android can reconnect the Notification Listener reliably after app updates or process cleanup.

## Provider status

Provider support must not be marketed as "verified" until a real incoming-payment notification has been validated.

- DANA Bisnis — verified with real incoming-payment notifications.
- ShopeePay Merchant — preset + Smart Learn calibration.
- GoPay Merchant — preset + Smart Learn calibration.
- SeaBank — preset + Smart Learn calibration.
- BCA mobile / myBCA — preset + Smart Learn calibration.
- Other providers — Advanced / Smart Learn mode.

## How to verify an APK

Using Android Build Tools:

```text
apksigner verify --print-certs infinity-qris-voice.apk
```

Confirm the certificate SHA-256 is exactly:

```text
19a021c195943d5b82bf466aa7e4a5c02c4bbf72a9070eba87e9a1c6a3d9b0d4
```

Then calculate the file SHA-256 and compare it with the matching release record in this repository.

## Distribution policy

- The official website is the public discovery, privacy, installation, and verification source.
- QRIS Voice download/update access is routed to the official Telegram bot `@InfinityDigitalStoreBot`.
- The bot verifies Infinity Base membership with Telegram before delivery and fails closed if the community is not registered or Telegram verification fails.
- Before sending build 3, the bot recalculates the release APK SHA-256 and blocks delivery if it differs from the published release hash.
- The official bot may deliver the exact signed APK directly after successful membership and integrity verification.
- Permanent public APK URLs are not the supported distribution path; old/direct APK routes are redirected to the community gate.
- Do not trust APK files forwarded by unknown Telegram accounts, mirrors or file-sharing sites.
- A release page must publish the version, build number, APK SHA-256 and signing-certificate fingerprint.
- A release must never silently change binary content while keeping the same published hash.
- If a new binary is built, it must receive a new Android `versionCode` before public distribution.

## Security / privacy questions

Use the support contact shown on https://infinityai.id/ or the official Telegram bot. Never send banking passwords, PINs or OTPs to support.
