# Submitting the App to iTunes Connect

## Create the Production Build

1. Clear out your prior build artifacts

   `$ rm -rf .meteor/local/cordova-build`
   `$ rm -rf ../<app-name>-build`

1. Create the build

   `$ meteor build ../<app-name>-build --server http://<app-server> --mobile-settings settings.json`

1. Deploy your server API to Modulus (or where ever)

   `$ modulus deploy`

Note that if you need to switch based on environment variables in your `mobile-config.js` file, like this:

```javascript
if (this.process.env.NODE_ENV === 'production') {
  App.configurePlugin('com.phonegap.plugins.facebookconnect', {
    APP_ID: 'XXXXXX', // production FB app ID
    APP_NAME: 'My App'
  });
}
else {
  App.configurePlugin('com.phonegap.plugins.facebookconnect', {
    APP_ID: 'XXXXXX', // test FB app ID
    APP_NAME: 'My App Development'
  });
}
```

then you can run your build like this:

`$ NODE_ENV=production meteor build ../<app-name>-build --server http://<app-server> --mobile-settings settings.json`




## Configure the App in Xcode

`open .meteor/local/cordova-build/platforms/ios/<app-name>.xcodeproj`

#### In the **General** tab:

- From the `Identity` section, select the appropriate team.

#### In the **Build Settings** tab:

- From the `Code Signing` section, `Code Signing Identity` > `Release`, select the appropriate **Distribution** profile.

<blockquote>
When Xcode logs into the Apple Developer portal, it will download all the provisioning profiles. A profile is tied to an Bundle ID and a certificate (among other things). The certificate is tied to a private key that lives on a single machine.
</blockquote>

#### Deployment Settings:

1. From the Deployment section, select **iOS 7.0** for the iOS Deployment Target.
1. Make sure no iOS device is plugged into your computer. Select **iOS Device** from the build target menu.

#### Create an Archive:

1. Select **Product menu > Archive**.
1. When the archiving is complete, the archive list opens. Click the archive you just made, and click **Validate**. Select the appropriate team. Click **Validate**.

#### Submit:

- If validation is successful, click **Submit** and follow the prompts.
