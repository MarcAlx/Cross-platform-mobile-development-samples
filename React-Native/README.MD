#React Native

Based on  : https://github.com/MathieuDebit/Djinnius
Which use : https://github.com/dropbox/djinni

Here's another sample code worth reading : https://github.com/boloutaredoubeni/Twenty48

## Get started

1. Follow the step [here](https://facebook.github.io/react-native/docs/getting-started.html)

2. Run the following commands (in Djinnius-master) :

       yarn install
       make ios

2. Launch 
 
       react-native run-android

       or

       react-native run-ios

#### Troubleshooting android

1. If you have the following error :

        `You have not accepted the license agreements of the 
        following SDK components:...`

    Create a simple project via `Android Studio` targeting the needed SDK then run it, `Android Studio` will prompt you to accept licence

2. If you have the following error :

       A problem occurred configuring project ':app'. > SDK location not found. Define location
    
    Run the following command : 
       
         export ANDROID_HOME=/Users/{USERNAME}/Library/Android/sdk
         
3. If you have the following line be fore launching the app : 

        /bin/sh: adb: command not found

    Run the following command : 

         export PATH=${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools

4. /!\ Makefile references 

        /Applications/android-ndk-r16/ for ANDROID_BUILD_TOP

5. In case of `Could not get BatchedBridge, make sure your bundle is packaged properly`

Run the following command : 
     
        adb reverse tcp:8081 tcp:8081

6. Export ANDROID_NDK :

        export ANDROID_NDK=/Applications/android-ndk-r16/

7. If you encounter (at compilation) time the following message :

       error: unknown warning option '-Wno-literal-suffix'; did you mean '-Wno-literal-range'? [-Werror,-Wunknown-warning-option]
    
    Replace all occurences of  `-Wno-literal-suffix` in `libhelloworld_jni.targer.mk` and `/deps/djinni/support-lib/djinni_jni.target.mk` (ie the two .mk define by GypAndroid.mk)

    E.G :

        LOCAL_CPPFLAGS_Release := \
	    -std=c++11 \
	    -frtti \
	    -fexceptions \
	    -Wno-literal-suffix

    Would be become :
        
        LOCAL_CPPFLAGS_Release := \
	    -std=c++11 \
	    -frtti \
	    -fexceptions

#### Troobleshooting iOS

1. If you have the following error :

        xcrun: error: unable to find utility "instruments", not a developer tool or in PATH

    Follow these [instructions](https://stackoverflow.com/a/39779171/5102373)

## Help

- http://blog.tylerbuchea.com/how-to-create-a-react-native-ios-native-module/

- https://github.com/googlesamples/android-ndk/tree/master/hello-jni

- https://shift.infinite.red/native-modules-for-react-native-android-ac05dbda800d

- https://facebook.github.io/react-native/releases/0.21/docs/native-modules-android.html

## Screenshot

ios

![](./screenshots/ios.png)

android

![](./screenshots/android.png)

***NB** "Hello World!" text is provided by native code*