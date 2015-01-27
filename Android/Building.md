# Building for Android

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
