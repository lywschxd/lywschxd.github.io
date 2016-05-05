# Lazy Foo' Productions

# Setting up SDL 2 on Mac Android



Disclaimer: I am not a professional Android developer, so my knowledge of Android is limited to doing some porting of SDL apps to Android. Unfortunately, most the documentation for Android/SDL assumes you're proficient
with the Android SDK and NDK. I may not be an expert with Android, but I can bridge the gap between SDL desktop development and SDL Android development.

[1)](#1) Get ready to download. A lot. Like around 1 gigabyte of data. If you have a limited connection, I'm sorry the android SDK is huge and it's just the way things are.
I recommend having a movie or TV show to watch ready if a gigabyte takes a long time for you to download.

First, download the Java Development Kit (JDK) on [this page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html):

![](images/download_jdk-1.png)

[2)](#2) Download the Android NDK on [this page](https://developer.android.com/ndk/downloads/index.html):

![](images/download_ndk-2.png)

[3)](#3) Download Apache Ant tar.gz archive on [this page](http://ant.apache.org/bindownload.cgi).

![](images/download_ant-1.png)

[4)](#4) Download the SDL2 source. Not just the development libraries you use for desktop development, the full source. You can find the full source on
[this page](https://www.libsdl.org/download-2.0.php).

![](images/download_sdl_source-2.png)

[5)](#5) Download the Android SDK Manager on [this page](https://developer.android.com/sdk/index.html). We're not going to use the installer. We just
want the SDK Manager files by themselves.

![](images/download_sdk_manager-2.png)

[6)](#6) Install the JDK. This should be a simple next, next, next,... finish installation.

[7)](#7) Create a folder to serve as your Android development directory. For this tutorial we will create ~/mac_android as our development directory.

After you have created your development directory, extract the NDK (it's going to take a while), Apache Ant, the SDL2 source, and the Android SDK manager. **Important**: The NDK is a self extracting binary, but
it need execution permissions to extract itself. Do grant it full permissions open a terminal in our Android development directory and run:
```bash
sudo chmod 777 android-ndk-r10e-darwin-x86_64.bin
```
After you extract everything, you should have the following
directories in your Android development directory:

*   ~/mac_android/android-ndk-r10d
*   ~/mac_android/apache-ant-1.9.4
*   ~/mac_android/android-sdk-macosx
*   ~/mac_android/SDL2-2.0.3

The version numbers might be a bit different like "~/mac_android/SDL2-2.0.4" or "~/mac_android/apache-ant-1.9.6", which is ok. What matters is that the Android NDK, Apache Ant, Android SDK, and the SDL2 source
are in this folder where you can find them.

[8)](#8) With everything extracted, run the SDK manager at ~/mac_android/android-sdk-macosx/tools/android. The SDK Manager will download the Android SDK tools we need. Yes, we still
have more stuff to download.

You may be tempted to download the latest version, but I recommend against that. Later versions aren't as stable as the earlier versions and I would only get them if you actually need the
features unique to them. I recommend getting the first stable release after API 12, which in this case is API 15.


Under the tools section, check "Android SDK Tools",  "Android SDK Platform Tools", and "Android SDK Build-Tools":

![](images/sdk_tools-2.png)

Under API 15, check "SDK Platform", and all the system images (especially ARM and Intel):

![](images/sdk_api_15-2.png)


You can download more than this, but keep in mind it can take hours more depending on your connection.

[8)](#8) Now that you have everything downloaded, it's time to configure your Mac to find the programs it needs to build Android apps. We do this by setting the PATH environment
variable which controls where OS X looks for executables. We do this by adding commands to the bash profile.

First make sure the bach profile file exists by using the touch command:
```bash
 touch ~/.bash_profile
```
Then open it for editing
```bash
 open ~/.bash_profile
```
What we want to do is whenever we run the ndk-build, ant, or adb commands, the OS should look where ndk-build, ant, or adb binaries are located. If you set up ~/mac_android like we did in this tutorial, they
should be at:

*   ndk-build - ~/mac_android/android-ndk-r10e
*   ant - ~/mac_android/apache-ant-1.9.6/bin
*   adb - ~/mac_android/android-sdk-macosx/platform-tools

**You'll probably be using a more recent version of these tools which means their paths will be slightly different. Double check the paths** by finding where the ndk-build, ant, and adb binaries are located. Once
you find where these programs are, add an export command to the bash profile:
```bash
 export PATH=$PATH:~/mac_android/android-ndk-r10e:~/mac_android/apache-ant-1.9.6/bin:~/mac_android/android-sdk-macosx/platform-tools:
```
**Each location should be separated by a colon.** After you appended the paths to ndk-build, ant, and adb, save the bash profile. Now every time you log in, it should load the bash profile and load the PATH
variable with the paths to the Android development binaries. However, we need the path to be loaded now so we need to reload the bash profile:
```bash
 source ~/.bash_profile
```
[9)](#9) Now it's time to test that we set the paths correctly. Open up ~/mac_android in the terminal.

Test ndk-build by typing in "ndk-build" and hitting enter. If you did it right you should get the following error:
```bash
 Android NDK: Could not find application project directory ! Android NDK: Please define the NDK_PROJECT_PATH variable to point to it.
```
If you did it wrong you'll get this error:
```bash
 bash: ndk-build: command not found
```
Test ant by typing in "ant debug" and hitting enter. If you did it right you should get the following error:
```bash
Buildfile: build.xml does not exist! Build failed
```
If you did it wrong you'll get this error:
```bash
 bash: ant: command not found
```
Test adb by typing in "adb help" and hitting enter. If you did it right you should get a large help prompt or it will try to connect to a Android device. If it tries that, hit cmd+c to exit the program.

If you did it wrong you'll get this error:
```bash
 bash: adb: command not found
```
[10)](#10) After the path is set up, we need to set up the JAVA_HOME environment variable so Ant can use the Java development tools. Open up the bash profile again and add
another line that sets the JAVA_HOME variable:
```bash
 export JAVA_HOME=$(/usr/libexec/java_home)
```
Save and reload the bash profile.

[11)](#11) Test the JAVA_HOME set up by entering "ant debug" into the console from your Android development directory. If you set it up right you should get the following error:
```bash
 Buildfile: build.xml does not exist! Build failed
```
If you set it up wrong you'll get this error:
```bash
 JAVA_HOME is not defined correctly.
```
[12)](#12) Next, we need to set up the ANDROID_HOME environment variable so Ant can build Android packages. Open up the bash profile one more time and add:
```bash
 export ANDROID_HOME=~/mac_android/android-sdk-macosx
```
[13)](#13) Go to the Android project directory in the SDL source folder we extracted. It should be located at ~/mac_android/SDL2-2.0.3/android-project. Open a terminal
in the directory and enter "ant debug". If you set up ANDROID_HOME correctly you should get the following error:
```bash
 ~/mac_android/android-sdk-macosx/tools/ant/build.xml:538: Unable to resolve project target 'android-12'
```
If you didn't set it up properly, you'll get:
```bash
 BUILD FAILED ~/mac_android/SDL2-2.0.3/android-project/build.xml:56: sdk.dir is missing. Make sure to generate local.properties using 'android update project' or to inject it through the ANDROID_HOME environment variable.
```
[14)](#14) This part is technically optional but highly recommended. See, you can test on your Android device or the emulator. The emulator sucks, so you're going to want to use
your Android device. You'll need to enable USB debugging on your device. That is version specific which is why I won't go over it here. Google search "android enable usb debugging" with your device name and
they'll show you how to do it.

[15)](#15) With our Android environment set up, it's time to get started. Go to the Android project directory inside of the SDL2 source folder
(~/mac_android/SDL2-2.0.3/android-project), open up a terminal and ndk-build. You should get the following error:
```bash
Android NDK: WARNING: APP_PLATFORM android-12 is larger than android:minSdkVersion 10 in ./AndroidManifest.xml
*** No rule to make target `jni/src/../SDL/src/main/android/SDL_android_main.c', needed by `obj/local/armeabi/objs/main/__/SDL/src/main/android/SDL_android_main.o'.  Stop.
```
We'll get rid of that error in a second but for now let's fix the warning. Open up AndroidManifest.xml in the project directory and change
```
 <uses-sdk android:minSdkVersion="10" android:targetSdkVersion="12" />
```
to
```
 <uses-sdk android:minSdkVersion="15" android:targetSdkVersion="15" />
```
Run ndk-build one more time in the project directory and you'll get the error without the warning:
```
*** No rule to make target `jni/src/../SDL/src/main/android/SDL_android_main.c', needed by `obj/local/armeabi/objs/main/__/SDL/src/main/android/SDL_android_main.o'.  Stop.
```
[16)](#16) In this case, the error "No rule to make target" actually means it can't find the file you're asking to compile. So what's actually going on is that the ndk is trying to build SDL_android_main.c but it can't find it at ~/mac_android/SDL2-2.0.3/android-project/jni/src/../SDL/src/main/android/SDL_android_main.c.

Let's back up a bit and talk about how SDL 2 on Android works. Android development is mostly Java based and SDL is a C based library. The **N**ative **D**evelopment **K**it that allows Java to interface with native C/C++ code using the **J**ava **N**ative **I**nterface. With the NDK, we'll build SDL2 as a **s**hared **o**bject that will interface with Java, and we'll build our game as another shared object that will interface with SDL 2.

In the android project directory there's a jni directory that will contain our native C/C++ code. Create a directory called SDL2 inside of the JNI directory. In this directory we will put the source, includes, and Android makefile for the SDL library. Copy src, include, and Android.mk from ~/mac_android/SDL2-2.0.3 and paste them inside of ~/mac_android/SDL2-2.0.3/android-project/jni/SDL2.

From the project directory run ndk-build. SDL should compile and install but you'll still get an error.

[17)](#17) The error:
```
 *** No rule to make target `jni/src/../SDL/src/main/android/SDL_android_main.c', needed by `obj/local/armeabi/objs/main/__/SDL/src/main/android/SDL_android_main.o'.  Stop.
```
Still means it can't find SDL_android_main.c, but this is part of our game compiling. We need to put our game source in the jni/src folder. Download the
[source for lesson 52](52_hello_mobile.zip) and place 52_hello_mobile.cpp at jni/src/52_hello_mobile.cpp.

Next open up the makefile for the game source at jni/src/Android.mk. Change
```bash
 SDL_PATH := ../SDL
```
to
```bash
SDL_PATH := ../SDL2
```
If you still get "No rule to make target" for SDL_android_main.c it means you messed up this part.

In Android.mk there should also be a section like this:
```bash
 LOCAL_SRC_FILES := $(SDL_PATH)/src/main/android/SDL_android_main.c 	YourSourceHere.c
```
Change YourSourceHere.c to 52_hello_mobile.cpp so it compiles our source.

Run ndk-build from the project directory and you should get a new error:
```bash
jni/src/52_hello_mobile.cpp:7:18: fatal error: string: No such file or directory
#include <string>
^
compilation terminated.
```
[18)](#18) That previous error is because this project is not set to use the C++ standard library, which is why it can't find the string header. To enable STL, open up jni/Application.mk and uncomment "APP_STL := stlport_static". Run ndk-build from the project directory. The SDL 2 library and our source should build the native binary.

[19)](#19) With SDL 2 and our SDL application libraries built, it's time to interface it with Java. First we need to configure Ant to use API 15\. In the project directory there should be ant.properties. Open it and add the line
```bash
 target=android-15
```
so Ant uses API 15\. from the project directory run ant debug. It will say build successful but **THE GAME WILL NOT RUN**. Be extra careful beyond this point because there aren't many useful error messages. The application will just stop working.

[20)](#20) Our project will build but not run at this point because we still need to interface the native code with Java, and it can't detect errors with that until it runs. First create a folder called com in the project folder's src directory. **NOT the JNI source directory at android-project/jni/src**, but the Java source directory at android-project/src. Inside of that folder, create another folder called tutorial. Inside that folder create a folder called game. You should now have a folder with the path android-project/src/com/tutorial/game.

Download a premade [Java file](HelloSDL2Activity.java) designed to interface with SDL and place it at android-project/src/com/tutorial/game/HelloSDL2Activity.java.

The contents of this source file are simple.
```java
package com.tutorial.game;
import org.libsdl.app.SDLActivity;
public class HelloSDL2Activity extends SDLActivity
{
}
```
All it does is create another class from the SDLActivity class which takes care of all the interfacing with SDL for us. Notice how the package name has to match the directory structure we created.

[21)](#21) Open AndroidManifest.xml. Change

```java
package="org.libsdl.app"
 //to
 package="com.tutorial.game"
```

and

```java
android:name="SDLActivity"
//to
android:name="HelloSDL2Activity"
```

Now the Android app will use our package and run our activity.

[22)](#22) Open ~/mac_android/SDL2-2.0.3/android-project/res/values/strings.xml and change
```
<string name="app_name">SDL App</string>
```
to
```
 <string name="app_name">SDL Tutorial</string>
```
This will change the name under the App's icon from SDL App to SDL Tutorial.

[23)](#23) At this point the app will run our code but it will fail because it can't load the media files for the tutorial. Media files go in the asset directory. Create a folder called "assets" in the project folder. Copy the directory inside of the zip we downloaded and place it in the assets directory. If the application needs to open "52_hello_mobile/hello.bmp", it needs to be at android-project/assets/52_hello_mobile/hello.bmp when building.

[24)](#24) Our SDL application is ready to build and run. Inside of the project directory, run "ant debug install". The application should build and install on your Android device. Search for it in your apps and run it. If the image is small it's because it's only 128x128 so it can fit the smallest Android device.

[25)](#25) If you want to get console output from your Android application, you'll have to use logcat with the **A**ndroid **D**e**b**ugger. With your device Android connected, run "adb logcat". You'll see all the things outputting to the console. When you first run it you'll get a flood of messages but after the initial flood you should see anything you write to the console. You can quit logcat with cmd+c.

Now that you have SDL 2 running on your device, it's time to go onto part 2 of the tutorial. Note: if you change the orientation of your Android device, the application will crash. We will deal with how to fix that in the next tutorial.

[Hello Mobile Part 2: Your First Mobile SDL 2 App](Your_First_Mobile_SDL2_App.md)
