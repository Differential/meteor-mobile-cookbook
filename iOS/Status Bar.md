# Status Bar Styles

- [Overview](#overview)
- [StatusBarOverlaysWebView](#StatusBarOverlaysWebView)
- [StatusBarStyle](#StatusBarStyle)
- [StatusBarBackgroundColor](#StatusBarBackgroundColor)
- [Dynamic Styles](#dynamic-styles)

## Overview
[http://devgirl.org](http://devgirl.org/2014/07/31/phonegap-developers-guid/) has a great demo of the different status bar options.

For best results, you typically want the following settings:

```
App.setPreference('StatusBarOverlaysWebView', 'true');
App.setPreference('StatusBarStyle', 'lightcontent');
```

Which results in a status bar that blends with the header and has white text and icons:
![](/Resources/images/status-bar-lightcontent.png)

----

## StatusBarOverlaysWebView

This setting determines wether the status bar blends in with the header or not. Typically you want `StatusBarOverlaysWebView` to be `true`. When set to `false`, you get a separate status bar area as shown below:

```
App.setPreference('StatusBarOverlaysWebView', 'false');
```

![](/Resources/images/StatusBarOverlaysWebView.png)

----

## StatusBarStyle

```
App.setPreference('StatusBarStyle', 'default');
```

The `default` and `blacktranslucent` values display **black** text and icons.

The `lightcontent` and `blackopaque` values display **white** text and icons.

### default

Dark content, intended for use on light backgrounds.

![](/Resources/images/status-bar-default.png)

### lightcontent

Light content, intended for use on dark backgrounds.

![](/Resources/images/status-bar-lightcontent.png)

### blacktranslucent

**Deprecated**: use `default` instead.

![](/Resources/images/status-bar-blacktranslucent.png)

### blackopaque

**Deprecated**: use `lightcontent` instead.

![](/Resources/images/status-bar-blackopaque.png)

----

## StatusBarBackgroundColor

If `StatusBarOverlaysWebView` is set to `false`, you can set a custom `StatusBarBackgroundColor` for the status bar.

```
App.setPreference('StatusBarStyle', 'false');
App.setPreference('StatusBarBackgroundColor', '#2C53AE');
```

![](/Resources/images/StatusBarBackgroundColor.png)

## Dynamic Styles

Sometimes you need to change the style of your status bar dynamically. For instance, if your status bar has white text and icons `StatusBarStyle = lightcontent`, but you open a modal that has a header bar with a light grey background, it would be nice to change the status bar to have black text and icons `StatusBarStyle = default`.


## How to hide the statusbar on app launch

During runtime you can use the StatusBar.hide function, but if you want the StatusBar to be hidden at app startup, you must modify your app's Info.plist file.

- After running build, go to the output directory and find `/[app]/[app]-Info.plist` file and open it.
- Copy / Paste values below, under the first `<dict>` tag.

```
<key>UIStatusBarHidden</key>
<true/>
<key>UIViewControllerBasedStatusBarAppearance</key>
<false/>
```

## How to do this in Meteor using the Cordova Statusbar Plugin

One way to manage Cordovia plugins is to use a local package. In your `package.js`, include the following:

```
Cordova.depends({
  'org.apache.cordova.statusbar': '0.1.9'
});
```

Now you have access to the [Cordova Statusbar Plugin](https://github.com/apache/cordova-plugin-statusbar) API. However, remember to wrap any calls in a `Meteor.startup` block.

```
Meteor.startup(function () {
  if(Meteor.isCordova){
    StatusBar.hide();
  }
});
```

For more information see [Meteor Cordova Phonegap integration](https://github.com/meteor/meteor/wiki/Meteor-Cordova-Phonegap-integration).
