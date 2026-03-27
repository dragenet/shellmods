# android-home

Sets up the Android SDK environment for CLI tools and emulators.

## What It Does

- Exports `ANDROID_HOME` pointing to `~/Library/Android/sdk`.
- Adds the following to `$PATH`:
  - `emulator`
  - `platform-tools` (adb, fastboot)
  - `cmdline-tools/latest/bin` (sdkmanager, avdmanager)

## Prerequisites

- Android SDK installed via Android Studio or standalone SDK tools at `~/Library/Android/sdk`.
