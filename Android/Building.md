# Building for Android

## Getting Started
Make sure you have all of the required software installed on your local machine. Follow these [instructions](https://github.com/meteor/meteor/wiki/Mobile-Development-Install:-Android-on-Mac).

## Setup mobile-config.js

Insure you have a `buildNumber` property added to your `App.info` settings inside your `mobile-config.js` file. For iOS, this can be created on the fly in XCode, but for Android APK's, it needs to be set here.

```
// inside mobile-config.js
App.info({
  ...
  version: '1.0.0',
  buildNumber: '100' // has to be a number
})
```

**Note:** 
For iOS, we typically increment the build number from 1 to 2 and so on. However, we noticed some issues when uploading APK's to Google play that it preferred a larger number. Test it out, but you might have to start the `buildNumber` at 100 or 101.


## Build the App
`$ meteor build ../<app-name>-build --server http://<app-server> --mobile-settings settings.json`

## Create a private key for the app:
```
keytool -genkey -alias <app-name> -keyalg RSA -keysize 2048 -validity 10000
```

## Sign the app:
```
cd .meteor/local/cordova-build/platforms/android/ant-build
jarsigner -digestalg SHA1 <app-name>-release-unsigned.apk <app-name>
~/.meteor/android_bundle/android-sdk/build-tools/21.0.0/zipalign 4 <app-name>-release-unsigned.apk <app-name>-release-signed.apk
```

## Submit the App
The submittable `.apk` file is located at:

```
.meteor/local/cordova-build/platforms/android/ant-build/<app-name>-release-signed.apk
```

Upload to [Google Play Developer Console](https://play.google.com/apps/publish)
