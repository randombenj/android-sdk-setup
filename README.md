# Android SDK setup

This document aims to provide a guide to setup the android sdk without
android studio, for example if you want to develop [flutter](flutter.dev) apps
in [vscode](https://code.visualstudio.com/).


**Install sdkmanager**

First you need the `sdkmanager` to download and manage all the other tools like the android emulator.
Go to the download page and download page (https://developer.android.com/studio/index.html#command-tools) and
download `sdk-tools-linux-*.zip`.

The folder **must be called**: `cmdline-tools/latest`, we will put it to `~/bin`.

***Note**: You will need to add `$HOME/bin/cmdline-tools/latest/bin:$HOME/bin/emulator` to your `PATH`*

**Install android dev tools using sdkmanager**

Now we need to install the required tools to create an android emulator:

```sh
# list available emulators
sdkmanager --list

# install an emulator
sdkmanager "system-images;android-30;google_apis;x86_64" "platforms;android-30" "build-tools;30.0.3" "platform-tools"
```

**Create an android emulator**

Now we can create an android emulator to develop our apps:

```sh
avdmanager create avd -n test -k "system-images;android-30;google_apis;x86_64"
```

**Start the emulator**

Finally we can start and use our emulator:

```sh
emulator @test
```

To use the emulator with flutter run:

```sh
flutter emulators --launch test
```
