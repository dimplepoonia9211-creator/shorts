# Financial Tech Android (APK)

This folder contains a **separate Android app source project**.
It does **not** modify the PC (PyQt) application.

## What this is
- Android app scaffold (Kotlin + Jetpack Compose)
- CapCut-like navigation flow:
  - Import
  - Edit
  - Captions
  - Export
- Video processing stub: `FFmpegKit` is already included as a dependency.

## What is NOT possible without a build machine
Generating an `.apk` requires an Android toolchain (Android SDK + JDK + Gradle).
If your local PC has no Android toolchain installed, you must build the APK on:
- Another PC that has Android Studio installed, or
- A cloud CI (recommended): GitHub Actions / Codemagic / Bitrise

This repo includes a GitHub Actions workflow you can use to build the APK without installing anything locally:
- `.github/workflows/build-android-apk.yml`

## Build (on any machine that has Android Studio)
Open this folder in Android Studio:
- `financial_tech/android_app/`

Then build:
- **Debug APK**: Build > Build Bundle(s) / APK(s) > Build APK(s)
- **Release APK**: Build > Generate Signed Bundle/APK

## Next steps for full feature parity
The current code is a scaffold. To reach full parity with the PC app, we still need:
- **Video pipeline** (FFmpegKit commands):
  - clip segmentation
  - 9:16 / 16:9 export
  - pulse effect
  - background music mix
  - save/share output
- **Captions pipeline**:
  - integrate on-device ASR (recommended: `whisper.cpp` via JNI)
  - generate subtitles and burn-in during export

If you want me to produce an APK for you **without installing anything locally**, the best option is:
- Create a GitHub repository
- I add a GitHub Actions workflow to build the APK and upload it as an artifact
