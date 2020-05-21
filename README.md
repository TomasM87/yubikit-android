# Yubico Mobile Android SDK (YubiKit)

The **YubiKit** is an Android library provided by Yubico to interact with YubiKeys on Android devices. The library supports NFC-enabled and USB YubiKeys.

The library includes a demo application implemented in Kotlin, the [YubiKit Demo App](./yubikit-android/tree/master/YubikitDemo), which provides a complete example of integrating and using all the features of the library in an Android project.

Changes to this library are documented in this [changelog](./yubikit-android/blob/master/Changelog.md).


## About

The YubiKit requires a physical key to test its features. Before running the included [demo application](./yubikit-android/tree/master/YubikitDemo) or integrating the YubiKit into your own app, you need a YubiKey or a Security Key by Yubico to test functionality.

**YubiKit** is multi-module library with following components:

[Yubikit](./yubikit/README.md) provides functionality to detect whether a YubiKey is plugged in or is connected over NFC.

[OATH](./oath/README.md) allows applications such as an authenticator app to store OATH TOTP and HOTP secrets on a YubiKey and generate one-time passwords.

[OTP](./otp/README.md) provides implementation classes to obtain Yubico OTPs via USB or NFC.

[PIV](./piv/README.md) provides an implementation of the Personal Identity Verification (PIV) interface.

[MGMT](./management/README.md) provides YubiKey management functionality, a subset of the API for personal customization of the YubiKey and the HMAC-SHA1 challenge-response.

All **YubiKit** modules have javadoc and sources deployed with the library archive. Use that documentation for a more detailed explanation of all the APIs methods, properties and parameters.


#### Note

The **YubiKit** consumes data from the token and translates it to the application for further processing. The **YubiKit** performs data validation for the purposes of creating valid responses to the application; however, content/logical validation and security decisions are outside the scope of the **YubiKit** and must therefore be handled by the application.


## Getting Started

To get started, you can try the [YubiKit Demo App](./yubikit-android/tree/master/YubikitDemo) as part of this library or start integrating the library into your own application. The YubiKit requires a physical key to test its features. Before starting to look at the SDK, make sure you have downloaded the zip file containing all the necessary assets for using the library.

#### Try the Demo

Use the [YubiKit Demo App](./yubikit-android/tree/master/YubikitDemo) to learn how to integrate the YubiKit for Android with your app. The Demo app, which is implemented in Kotlin, shows several examples of how to use YubiKit, including WebAuthn/FIDO2 over the accessory or NFC YubiKeys. It shows how the library is linked with a project so it can be used for a side-by-side comparison when adding the library to your own project.

Open the YubiKitDemo Android Studio project and run it on a real device or an emulator to see the features.

#### Integrate the Library

The YubiKit SDK is available as a set of libraries and can be added as a dependency to your Android project. To add it using Android Studio or to add it manually, see [StackOverflow on adding a library project](https://stackoverflow.com/questions/16588064/how-do-i-add-a-library-project-to-android-studio).


###### Adding the Library

To add an external Android library to your project (called for these purposes "MyProject" and assuming your project structure created by Android Studio is as follows:

....
MyProject/
      app/
           - build.gradle  // local Gradle configuration (for app only)
           ...
      - build.gradle // Global Gradle configuration (for whole project)
      - settings.gradle
      - gradle.properties
....

*Step 1* (Optional) In the root directory (MyProject/), create new folder to keep a clean project structure: `/libs` into which the external libraries will be placed.

*Step 2* Download the Android SDK YubiKit ZIP from GitHub, rename the library directory if desired, and paste your library into the newly created `/libs` folder. The project's new structure is thus:
MyProject/
      app/
           - build.gradle  // Local Gradle configuration (for app only)
           ...
      libs/
           PagerSlidingTabStrip/
                - build.gradle // Local Gradle configuration (for library only)
      - build.gradle // Global Gradle configuration (for whole project)
      - settings.gradle
      - gradle.properties
      ...

#### Use the Library


## FAQ <a name="faq"></a>

#### Q1. Does the YubiKit work with all versions of Android?

A1. All YubiKit modules should work on Android API 19+. Yubico typically tests and supports n-1 per https://en.wikipedia.org/wiki/Android_version_history.

#### Q2. How can I debug my app on Android when a YubiKey takes up the USB port?

A2. You can set up Android Debug Bridge (adb) debugging over WiFi: https://developer.android.com/studio/command-line/adb#wireless

#### Q3.  Why is the USB device permissions prompt being shown every time the YubiKey is connected?

A3. This is an Android limitation. Android deals with these permissions at the OS level, and the only workaround is to use an intent filter as described in the Android Developers Guide [USB Host Overview](https://developer.android.com/guide/topics/connectivity/usb/host.html#using-intents). However, while this gets rid of the permissions prompt, it also causes your app to launch automatically whenever the YubiKey is connected.


## **Additional resources**

1. Yubico - [Developers' website](https://developers.yubico.com)
2. Yubico - [Online Demo](https://demo.yubico.com) for OTP and U2F
3. Yubico - [OTP documentation](https://developers.yubico.com/OTP)
4. Yubico - [What is U2F?](https://developers.yubico.com/U2F)
5. Yubico - [YKOATH Protocol Specifications](https://developers.yubico.com/OATH/YKOATH_Protocol.html)
6. FIDO Alliance - [CTAP2 specifications](https://fidoalliance.org/specs/fido-v2.0-ps-20190130/fido-client-to-authenticator-protocol-v2.0-ps-20190130.html)
7. W3.org - [Web Authentication: An API for accessing Public Key Credentials](https://www.w3.org/TR/webauthn/)
8. Android Developers site - [developer.android.com](https://developer.android.com)
