- If you're having any weird simulator issues. Clean out your local Cordova build:
  - Quit your Meteor server
  - Close Xcode
  - Run `rm -rf .meteor/local/cordova-build`
  - In iOS simulator menu, click iOS Simulator, then `Reset content & settings...`
  - Run `meteor run ios-device`

- Running `meteor run ios` will launch the simulator but not xcode. This was very flaky for me as the sim opened up a iPhone 4S, and it was a pain to switch to 5S or 6 every time. Also, HCR or re-running the app entirely, sometimes did not pick up changes. Running `meteor run ios-device` seemed to work more reliably, with the added bonus of seeing log messages in the Xcode terminal.

- If you are doing iOS Cordova debugging and have the Safari Develop Menu enabled, you can access the currently active session through the built-in Safari Web Inspector. To activate, go to Develop -> (iPad || iPhone) Simulator (normally, the third menu item) and click the active session you want to connect to. Voila!
