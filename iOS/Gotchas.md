# iOS Gotchas

## iPhone 6 scaling

By default, Meteor and Cordova will cause your UI to be scaled up on iPhone 6 and iPhone 6 Plus devices. To avoid this, change your `Launch Screen File` to `MainViewController.xib` in Xcode before building your app.

![](/Resources/images/iphone6-scaling.png)
