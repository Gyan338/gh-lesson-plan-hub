# GH Lesson Plan Hub — Android app

The hub packaged as an Android app. Own icon, no browser bar, works with the phone in
flight mode.

Powered by RiGAd DigiPress & I.T Consortium.

---

## First, the honest bit

An APK has to be **compiled**, and that needs Google's Android build tools. This folder is
the complete project; turning it into an installable `.apk` is one build step. Route 1
below does that on GitHub's free servers in about five minutes with nothing installed on
your side.

---

## Route 1 — build it in the cloud (no Android Studio)

1. Create a free GitHub account.
2. New repository, name it `gh-lesson-plan-hub`, and upload this whole folder.
3. Open the **Actions** tab. The build starts on its own.
4. When it finishes, open the run and download **GH-Lesson-Plan-Hub-app** from Artifacts.
5. Inside the ZIP is `app-debug.apk`. That is the file you send to teachers.

Change `index.html` and upload again, and a fresh APK is built each time.

## Route 2 — Android Studio

**File → Open** this folder, wait for the first sync, then
**Build → Build Bundle(s) / APK(s) → Build APK(s)**.
The file appears in `app/build/outputs/apk/debug/app-debug.apk`.

## Route 3 — command line

With Java 17 and the Android SDK installed:

```bash
cd GHLessonPlanHubApp
./gradlew assembleDebug
```

---

## Sending it to teachers

Send `app-debug.apk` on WhatsApp, by Bluetooth, or on a pen drive. The teacher taps it,
allows installing from that source, and the icon appears. Android 5.0 and newer.

The app is about 2 MB and carries the whole curriculum and your logo inside it, so a
teacher can install it and use it without ever going online.

---

## What the app adds over the browser version

- **Word downloads land in the phone's Download folder.** After each one the app offers
  **Open** (in Word or WPS) or **Send** (straight to WhatsApp), so a teacher can produce a
  lesson plan and send it to the head teacher without leaving the phone.
- **Printing goes through Android's print service** — any Wi-Fi or Bluetooth printer with
  its maker's plugin, or **Save as PDF**. Schemes print landscape automatically, lesson
  plans portrait.
- **The WhatsApp buttons open WhatsApp itself**, with the class and device code already
  written into the message. If WhatsApp is not installed the app says so rather than failing
  quietly.
- **Copying an access key opens Android's share sheet**, so you can send a key straight to
  the teacher from the Issue Keys screen.
- **The connection pill reads the real network state** from Android rather than guessing.

---

## Licences on Android

Each installation has its own device code, shown on the sign-in screen, and a device-locked
key opens on that phone only.

**One thing to tell teachers:** clearing the app's data or uninstalling it wipes the device
identity, so the old key stops working. If that happens, open **Licences → Release** on your
side and issue a fresh key against their new device code. Backing up their content pack
first is worth the trouble.

---

## Changing it later

- **The hub itself** — edit `app/src/main/assets/index.html` and rebuild. It is the same
  file that runs in a browser, so both versions stay in step.
- **App name** — `app/src/main/res/values/strings.xml`.
- **Icon** — the `ic_launcher` images in the `mipmap-*` folders.
- **Version** — `versionCode` and `versionName` in `app/build.gradle`. Raise `versionCode`
  by one for every update you send out, or phones will refuse to install over the old copy.
