# Infinity QRIS Voice — Release Checklist

A public QRIS Voice release is ready only when all checks below pass.

## Android build identity

- [ ] Android `versionCode` is higher than the previous public release.
- [ ] `versionName` matches the website, Telegram bot, and release record.
- [ ] Package name is exactly `com.infinity.qrisvoice`.
- [ ] Release APK is signed with the official Infinity certificate.
- [ ] Signing certificate SHA-256 matches:
  `19a021c195943d5b82bf466aa7e4a5c02c4bbf72a9070eba87e9a1c6a3d9b0d4`.
- [ ] Full unit-test suite passes.
- [ ] Release APK installs as an in-place update over the previous official APK.

## Reliability checks

- [ ] Notification Listener connects after installation.
- [ ] DANA real incoming-payment notification is detected.
- [ ] Transaction is written to local history once.
- [ ] Audio announcement plays once.
- [ ] Duplicate notification ID reuse does not suppress a new payment.
- [ ] Xiaomi / Redmi / POCO onboarding explains Auto-start / Mulai Otomatis.
- [ ] After an APK update on HyperOS, the app asks the user to review Auto-start again.
- [ ] A short listener gap recovers a recent active payment without duplicating it.

## Privacy / trust copy

Website and Telegram copy must state only capabilities that are actually implemented.

Required wording principles:

- The app is **native Android**, not PWA.
- Payment processing and history are local to the Android device.
- Notification Access is required to detect payment notifications.
- SMS, contacts, location, bank password, PIN and OTP are not required for the payment-listener workflow.
- Smart Learn observations are temporary and local.
- Do not claim a provider is verified until a real incoming-payment notification has been validated.
- If ads are not currently enabled, say **"currently without ads"**, not a permanent promise.

## Provider labels

Current release labels:

- DANA Bisnis — verified with real incoming-payment notifications.
- ShopeePay Merchant — preset + Smart Learn.
- GoPay Merchant — preset + Smart Learn.
- SeaBank — preset + Smart Learn.
- BCA mobile / myBCA — preset + Smart Learn.
- Other providers — Advanced / Smart Learn.

Do not advertise Mandiri, OVO, or another provider as supported until its parser/preset has been implemented and validated.

## Distribution

- [ ] Direct old/stale APK URLs are removed or redirected.
- [ ] Website download is gated through the official Telegram bot if community membership is required.
- [ ] Telegram bot verifies group membership with Telegram before delivery.
- [ ] Telegram bot verifies the release APK SHA-256 immediately before delivery and fails closed on mismatch.
- [ ] The exact signed APK is delivered only by the official bot after membership + integrity verification.
- [ ] A permanent public APK URL is not exposed as the supported download path.
- [ ] Website shows version, Android requirement, APK SHA-256, and signer fingerprint.
- [ ] Privacy policy and installation guide are linked beside the download action.

## Telegram community gate

Official bot: `@infinitydigitalstorebot`

Official community invite:
`https://t.me/+W6H55z8tjwY0Njc1`

Recommended flow:

1. User opens QRIS Voice page.
2. User presses **Gabung Komunitas & Unduh Gratis**.
3. Website opens the official bot with a QRIS Voice deep-link payload.
4. Bot shows the official group invite and a **Saya Sudah Bergabung** button.
5. Bot checks Telegram membership.
6. Only verified members receive the exact release APK from the official bot.
7. Before delivery, the bot checks the APK SHA-256 against the published release record.
8. App operation itself remains offline-first and does not require continuous Telegram membership.

## Public release record

For every new release create:

`qris-voice/releases/<version>-build<versionCode>.json`

Minimum fields:

- product
- package_name
- version_name
- version_code
- apk_filename
- apk_sha256
- signer_certificate_sha256
- min_sdk
- target_sdk
- published_apk_size_bytes
- release timestamp / notes

Never replace the binary behind a published release record without creating a new version/build record.
