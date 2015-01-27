# Building for iOS

## Build the App
`$ meteor build ../<app-name>-build --server http://<app-server> --mobile-settings settings.json`

## Configure the App in Xcode

`open .meteor/local/cordova-build/platforms/ios/<app-name>.xcodeproj`

#### In the **General** tab:

- From the Identity section, select the appropriate team.

#### In the **Build Settings** tab:

- From the Code Signing section, Code Signing Identity > Release, select the appropriate **Distribution** profile

#### Deployment Settings:
- From the Deployment section, select **iOS 7.0** for the iOS Deployment Target.

- Make sure no iOS device is plugged into your computer. Select **iOS Device** from the build target menu.

#### Create an Archive:
- Select **Product menu > Archive**.

- When the archiving is complete, the archive list opens. Click the archive you just made, and click **Validate**. Select the appropriate team. Click **Validate**.

#### Submit:
If validation is successful, click **Submit** and follow the prompts.
