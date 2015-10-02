# Device Debugging

First, ensure you have an Android device connected and are running your app via `meteor run android-device`.

## Remote Debugging

To remote debug your Android app in Chrome, navigate to [chrome://inspect/#devices](chrome://inspect/#devices) and enable "Discover USB devices". You should see your device in the list below and can launch the inspector by clicking "Inspect".

## Logs

You can tail the device's logs using the following command:

```
$ adb logcat
```
