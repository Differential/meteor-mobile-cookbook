# iOS Gotchas

## iPhone 6 scaling

By default, Meteor and Cordova will cause your UI to be scaled up on iPhone 6 and iPhone 6 Plus devices. To avoid this, change your `Launch Screen File` to `MainViewController.xib` in Xcode before building your app.

![](/Resources/images/iphone6-scaling.png)

## Xcode: Process launch failed - Security

If you experience a "Xcode: Process launch failed - Security" error in Xcode followed by an "Untrusted App Developer" error on your device, you likely have "stale" Provisioning Profiles on your device. To remove them:

- Connect your device to your computer
- In Xcode, select Windows > Devices
- Right-click on your device in the right hand list
- Choose "Show Provisioning Profiles"
- Delete all the profiles, or the profiles you can identify as being stale.
- Reinstall the app on your device
