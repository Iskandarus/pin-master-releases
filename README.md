# PinMaster releases

Builds of PinMaster, a GUI downloader for Pinterest boards. The source code
lives in a private repository; this one carries nothing but the binaries and
the notes that go with them.

Every release is one version built for five platforms, so a file is only ever
missing if that build failed.

**[Latest release](../../releases/latest)**

## Which file

| Platform | File |
| --- | --- |
| Windows 10/11 | `PinMaster-<version>-win64.zip` - portable, unpack and run `pin_master.exe` |
| macOS 10.15+ | `PinMaster-<version>-macos.zip` |
| Linux x64 | `PinMaster-<version>-linux-x64.tar.gz` |
| Android | `PinMaster-<version>-arm64-v8a.apk`, or `-android.apk` when unsure which ABI |
| iPhone / iPad | `PinMaster-<version>-ios-unsigned.ipa` |

## What each platform asks of you

**Windows.** Nothing. The archive carries the Visual C++ runtime it needs.

**macOS.** The app is not signed with a Developer ID and not notarised, so the
first launch is refused. Move it to Applications and drop the quarantine flag
the browser attached:

```
xattr -dr com.apple.quarantine /Applications/PinMaster.app
```

**Linux.** Video playback goes through libmpv, a system library the archive
cannot carry:

```
sudo apt-get install libmpv2   # or: sudo apt-get install mpv
```

Run `./pin_master` from the unpacked folder, or `./install.sh` to also get an
entry in the applications menu.

**Android.** The APKs are signed with the project's own release key, not the
Play Store's. Installing one means allowing installs from unknown sources once.

**iPhone / iPad.** The .ipa is unsigned, which is as far as a build without a
paid Apple Developer account can go. Install it with AltStore or Sideloadly,
which sign it with your own Apple ID on the way in. An app signed that way
stops launching after seven days and has to be re-signed.
