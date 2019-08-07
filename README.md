# Android SDK setup

This document aims to provide a guide to setup the android sdk without
android studio, for example if you want to develop [flutter](flutter.dev) apps
in [vscode](https://code.visualstudio.com/).

**Use java <= 8**

We need to use java <= 8 because newer versions don't work with the android sdk anymore! Check by running:

```
$ java -version
openjdk version "11.0.4" 2019-07-16
OpenJDK Runtime Environment (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3)
OpenJDK 64-Bit Server VM (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3, mixed mode, sharing)
```

You need to run `sudo update-alternatives --config java` and set it to */usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java*.
If you can't choose *java 8* you may need to install it `sudo apt install openjdk-8-jdk`

Finally you will need to set your `JAVA_HOME` to `/usr/lib/jvm/java-8-openjdk-amd64`.

```sh
export JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
```

**Install sdkmanager**

First you need the `sdkmanager` to download and manage all the other tools like the android emulator.
Go to the download page and download page (https://developer.android.com/studio/index.html#command-tools) and
download `sdk-tools-linux-*.zip`.

You can install them anywhere, in this example we will use `~/bin/android-sdk`

*Note: You will need to add `~/bin/android-sdk/tools/bin` to your `PATH`*

**Install android dev tools using sdkmanager**

Now we need to install the required tools to create an android emulator:

```sh
sdkmanager "system-images;android-29;google_apis;x86_64" "platforms;android-29" "build-tools;29.0.1" "platform-tools"
```

*Note: You can list available versions by running `sdkmanager --list`
You may also want to add `~/bin/android-sdk/emulator` and `~/bin/android-sdk/platform-tools` (adb) to your `PATH`*


**Create an android emulator**

Now we can create an android emulator to develop our apps:

```sh
avdmanager create avd -n test -k "system-images;android-29;google_apis;x86_64"
```

**Start the emulator**

Finally we can start and use our emulator:

```sh
emulator @test
```
