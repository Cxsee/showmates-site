# showmates.app

Public website of the Showmates app: landing page, privacy policy, terms of use and account deletion page, in Italian (`it/`) and English (`en/`). Served by GitHub Pages on the custom domain showmates.app.

The source lives in the private app repository (`site/`); this repository only publishes it.

Contact: support@showmates.app

## App Links: the fingerprints in `.well-known/assetlinks.json`

`assetlinks.json` lets Android open `showmates.app/u/…`, `/l/…`, `/t/…`, `/c/…`, `/tr/…`, `/daily` and `/try` directly in the app (package `app.showmates`). Each SHA-256 fingerprint is a signing certificate allowed to claim those links:

| Fingerprint (SHA-256) | Key | How it was checked |
|---|---|---|
| `BD:C3:2C:91:…:7C:69:C9` | Google Play app signing key (the one users' installs from Play are signed with) | Not verifiable locally: compare with Play Console → Test and release → App integrity → App signing → "App signing key certificate" |
| `C9:A8:80:5C:…:B7:29:AA` | Upload key (`showmates-upload.jks`, alias `upload`, created 13/10/2026) | `keytool -printcert -jarfile app-release.aab` on the release bundle (17/10/2026) |
| `D0:E0:4A:A9:…:E3:97:92` | Android debug key of the development PC (`%USERPROFILE%\.android\debug.keystore`) | `keytool -list -v -keystore debug.keystore -alias androiddebugkey -storepass android` (17/10/2026) |

The debug fingerprint is there only so debug builds on the emulators open the links. Remove it before the public launch (anyone holding that debug keystore could claim the links). If a key changes, update both the file and this table.
