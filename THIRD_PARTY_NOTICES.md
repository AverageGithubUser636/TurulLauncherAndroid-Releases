# Third-party notices

TurulLauncher's own code is original work by TurulNetwork. The following
third-party components are used as libraries or referenced as upstream work.

Full license texts are in [`licenses/`](licenses/): LGPL-3.0, Apache-2.0,
MIT, BSD-2-Clause and EPL-1.0.

## Libraries (Gradle dependencies)

| Component | License |
|---|---|
| AndroidX (core-ktx, activity, lifecycle, navigation, datastore, security-crypto) | Apache-2.0 |
| Jetpack Compose + Material 3 | Apache-2.0 |
| Kotlin stdlib, kotlinx.coroutines, kotlinx.serialization | Apache-2.0 |
| OkHttp / Okio (Square) | Apache-2.0 |
| JUnit 4 | EPL-1.0 |

## Bundled runtime: Amethyst-Android (since 0.6.0)

The local Gradle module `runtime/` is a vendored copy of
**Amethyst-Android** `v3_openjdk`, checked out from
https://github.com/AngelAuraMC/Amethyst-Android at commit
`28d6e12d68121b7dd75f2e841058a6b7cdfe4a29` on 2026-11-02.

- Copyright: © AngelAuraMC and Amethyst-Android contributors.
- License: **GNU Lesser General Public License v3.0**. The full text is
  `runtime/LICENSE` and `licenses/LGPL-3.0.txt`.
- Included: Java sources under `runtime/src/main/java` (Amethyst launcher,
  JRE handling, LWJGL3 Android GLFW bridge, controls, renderers, utilities),
  resources, assets (`components/`), and the Amethyst `exp4j` jar.
- Local modifications are documented in `docs/RUNTIME.md` and the source files
  (dynamic storage paths, non-SDL game activity, responsive R class support,
  system-GLES renderer defaults, archive-safe bootstrap). These modifications
  remain LGPL-3.0.
- Corresponding source: the complete LGPL-covered source for each published
  APK is attached to the matching GitHub release as
  `turul-runtime-source-<version>.tar.gz`, together with this notice and the
  license texts. The pinned upstream commit above is also available from the
  Amethyst-Android repository. Contact the TurulNetwork developers if an
  archive is missing or unreadable.

### Native and asset libraries from the Amethyst AARs

`runtime/src/main/jniLibs/arm64-v8a/` and `runtime/src/main/assets/` contain
redistributable libraries taken from the pinned Amethyst checkout. Their
license texts are shipped in `runtime/src/main/assets/licenses/`:

- **ANGLE** (`libEGL_angle.so`, `libGLESv2_angle.so`) — BSD-3-Clause.
- **Mesa / Kopper / Zink** (`libEGL_mesa.so`, `libglxshim.so`, `libglapi.so`,
  `libzink_dri.so`) — Mesa license (MIT plus component notices).
- **MobileGlues** (`libmobileglues.so`) — LGPL-2.1.
- **OpenAL Soft** (`libopenal.so`) — LGPL-2.0-or-later; OBOE/APACHE2 and
  PFFFT notices included.
- **SDL** (`libSDL2.so`, `libSDL3.so`) — zlib license; sdl2-compat notice.
- **imgui-java** (`libimgui-java.so`) — MIT; stb/nanovg/freetype/shaderc/vma
  notices included.
- **SPIRV-Cross** (`libspirv-cross-c-shared.so`) — Apache-2.0.
- **zstd-jni** (`libzstd-jni-1.5.7-6-dhcompat.so`) — BSD-2-Clause; zstd GPLv2
  notice included.
- **LWJGL 3.3.3/3.4.1** jars and Android natives (`liblwjgl*.so`,
  `libfreetype.so`, `libshaderc.so`) — BSD-3-Clause; license text included.
- **SimpleFPEWrapper** (`libSimpleFPEWrapper.so`) — from the pinned Amethyst
  build; see the upstream repository for its notice.

## Bundled native JNI libraries (since 0.3.0)

`app/src/main/jniLibs/arm64-v8a/` ships these shared libraries built from
Amethyst-Android `v3_openjdk` commit
`330c6eae3164df64bdc4828e946a9e62cc5169e4` (LGPL-3.0, © AngelAuraMC and
contributors; `androidnsbypass` © alexytomi, BSD-2-Clause per its repo;
bytehook © ByteDance, MIT):

- `libpojavexec.so`, `libexithook.so`, `liblinkerhook.so`,
  `libpojavexec_awt.so`, `libawt_xawt.so` (+ build-only `libawt_headless.so`)
- `libandroidnsbypass.so` (built from the pinned submodule commit
  `9f57982abf007aacc45becfc9328ae06fa6bbe3b`)
- `libbytehook.so` 1.1.2 (ByteDance, MIT, from Maven Central)
- `libshadowhook.so` 1.1.1 (ByteDance, MIT, `com.bytedance.android:shadowhook:1.1.1`,
  required by ByteHook; extracted from the Maven Central AAR)
- `libc++_shared.so` (NDK LLVM libc++, Apache-2.0 with LLVM exception)

Reproducible build recipe: `docs/RUNTIME_BUILD.md` (R2). Corresponding
source: the upstream repositories at the commits above.

## Java runtime (downloaded by the user, not bundled in the APK)

The Settings screen downloads OpenJDK Android builds from
`https://github.com/AngelAuraMC/angelauramc-openjdk-build` (tags
`download_jre8`/`17`/`21`/`25`). Those binaries are **GPLv2 with the Classpath
Exception** and remain subject to their upstream license; the launcher only
downloads and extracts the user-selected archive after verifying the release
SHA-256 digest. The corresponding source is published by the upstream project.

## Trademarks

Minecraft is a trademark of Mojang AB. Microsoft, Xbox are trademarks of
Microsoft. This project is not affiliated with or endorsed by Mojang or
Microsoft. TurulNetwork is not affiliated with Mojang or Microsoft.
