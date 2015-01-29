```
$ adb logcat
```

If you're having any weird simulator issues. Clean out your local Cordova build:
- Quit your Meteor server
- Close Xcode
- Run `rm -rf .meteor/local/cordova-build`
- In iOS simulator menu, click iOS Simulator, then `Reset content & settings...`
- Run `meteor run ios-device`
