# TurulLauncher Android – Releases

Installable APK builds of **TurulLauncher Android**, a Minecraft Java launcher
for ARM64 Android devices.

## Download the latest version

**Stable direct link:**

https://github.com/AverageGithubUser636/TurulLauncherAndroid-Releases/releases/latest/download/TurulLauncher.apk

Open this link on your phone. GitHub always serves the APK attached to the
newest release; the filename stays `TurulLauncher.apk`.

Current version: **0.6.4 (versionCode 14)**
Size: **138,575,368 bytes (~138.6 MB)**
SHA-256: `BFB8BC154BA98BE0B9A58AE7ACBFCA001C89F20705F6387235A1C073353832EC`

## Install

1. Open the download link on the phone.
2. Allow your browser/file manager to install unknown apps when Android asks.
3. Open the downloaded `TurulLauncher.apk` and install it.
4. Start TurulLauncher.
5. In **Settings → Runtime**, download the Java runtime required by the
   Minecraft version you want to play (Java 8 for legacy versions, 17/21/25 for
   modern versions).
6. Install a Minecraft version from the **Versions** screen, sign in with
   Microsoft (or create an offline profile), then press **Play**.

Requirements:

- ARM64 Android device (`arm64-v8a`, `aarch64`)
- Android 8.0 (API 26) or newer
- At least 4 GB RAM recommended; more for modern versions
- About 1 GB free storage for the app, Java runtime and game files

Upgrades: install newer releases over the existing app. Do not uninstall first;
your profiles and game files are kept in app-private storage. All public
releases are signed with the same TurulLauncher release key.

## What is included

- Real ARM64 Minecraft Java runtime host built on Amethyst-Android
  (LGPL-3.0), with JVM launch, LWJGL3, system GLES rendering and touch controls.
- In-app Java runtime download with SHA-256 verification.
- Version, library and asset installation with checksum verification.
- Microsoft sign-in and offline profiles.
- Internal storage only; no broad storage permission.
- Every bundled and downloaded native library is prepared for 16 KB page
  devices (ELF64 `p_align = 0x4000`).

## Current limitations

- **No physical ARM64 device test is available in the build environment yet.**
  The APK builds, its native libraries verify as 16 KB compatible, and the
  launch pipeline is wired end-to-end, but the actual JVM/EGL/JNI/game launch
  still needs a real-device run.
- Vanilla Minecraft versions only. Fabric/Forge/NeoForge are not implemented.
- Only the `opengles_system_gles` renderer is exposed.
- Minecraft online play requires a Microsoft account and a valid game
  entitlement. Offline mode is only for profiles that were verified online
  before.

## Source, licenses and notices

- Main source repository (private): https://github.com/AverageGithubUser636/TurulLauncher-Android
- Runtime source for this release is attached as
  `turul-runtime-source-0.6.4.tar.gz` to the release.
- The bundled Amethyst-Android runtime is LGPL-3.0. Its license and third-party
  notices are included in the source archive and in `THIRD_PARTY_NOTICES.md`.
- Minecraft is a trademark of Mojang AB. This project is not affiliated with or
  endorsed by Mojang or Microsoft.

## For maintainers

Each new version should:

1. Bump `versionCode` and `versionName` in the main repository.
2. Build a **signed** release APK:
   `./gradlew :app:assembleRelease`
3. Verify the APK: `apksigner verify`, `zipalign -c -P 16`, ELF 16 KB check.
4. Copy it here as `TurulLauncher.apk`.
5. Create a new GitHub release with a `vX.Y.Z` tag and upload:
   - `TurulLauncher.apk`
   - `turul-runtime-source-X.Y.Z.tar.gz`
   - `SHA256SUMS.txt`
6. Update `LATEST.txt` and this README with the version, size and SHA-256.

The signing key is **not** stored in this repository. Keep the keystore and
`signing.properties` backed up privately; losing them prevents future releases
from upgrading existing installations.
