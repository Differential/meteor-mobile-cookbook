# Splash Screens

## Set Icons
See: http://docs.meteor.com/#/full/App-icons

NOTE: Icons aren't working exactly right in `mobile-config.js`. Following the above docs will fail during validation because Apple will not find the correctly sized icon files. Meteor issue and workaround: https://github.com/meteor/meteor/issues/3153

## Set Splash Screen
See: http://docs.meteor.com/#/full/App-launchScreens

## Launch Screen Control
You can take control over when the launch screen/ splash screen is displayed. Adding the package `launch-screen`
Github: https://github.com/meteor/meteor/tree/devel/packages/launch-screen

## Reload-on-Resume

You can add the `mdg:reload-on-resume` package so that the app doesn't unexpectedly reload on the user:  https://github.com/meteor/mobile-packages/tree/master/packages/mdg:reload-on-resume
