# iOS Push Notifications

## raix:push
Github: https://github.com/raix/push

This package has been tested and is being used in production on an iOS app.

**Note**: As of v2.5.1 of this package I've found an issue with using `config.push.json` (specifically getting stuck on the loading screen) which requires the following workaround. This may have been fixed already (v2.6.0 at time of writing) but has not been tested yet. See this issue as reference: https://github.com/raix/push/issues/21

Somewhere on the server have the following:
```javascript
Push.Configure({
  apn: {
    passphrase: 'xxxx',
    certData: Assets.getText('cert.pem'),
    keyData: Assets.getText('key.pem'),
  },
  production: false // Should be true when using your production certificate and key
});
```

And on the client:
````javascript
Push.Configure({});
````

Make sure to check out the package documentation: https://github.com/raix/push/tree/master/docs

### Development
Follow directions [here](https://github.com/raix/push/blob/master/docs/IOS.md) or [here](http://www.raywenderlich.com/32960/apple-push-notification-services-in-ios-6-tutorial-part-1) to get set up with your App Id and development provisioning profile.

### Production
Follow the same directions as above for your provisioning profile but use the following to test your production certificate and key:
`openssl s_client -connect gateway.push.apple.com:2195
    -cert PushChatCert.pem -key PushChatKey.pem`

To test your production certificate and keys create an "Ad-Hoc" provisioning profile. This will let you use the production certificate and key in testing.


### Debugging
- Make sure that you set an explicit App Id. For example: com.differential.test123. A wildcard id (com.differential.\*) will NOT work for push notifications.
- Make sure you selected the proper team
- Make sure you select the proper provisioning profile (Development, Ad-Hoc, Production depending on your environment)

## Further Reading
- https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/CommunicatingWIthAPS.html
