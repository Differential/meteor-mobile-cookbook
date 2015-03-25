## Add sound

You can add sound to your app by using the cordova Media plugin api.

## Gotchyas

How do you reference the local file path?

```
var getLocalPath = function (localPath) {
  return cordova.file.applicationDirectory.replace('file://', '') + 'www/application/' + localPath.substr(1);
};

// in your app the path is public/assets/audio/theme.mp3
var src = getLocalPath('/assets/audio/theme.mp3');

var media = new Media(src, function () {});

// iOS will keep playing even when the screen is locked by default
media.play({playAudioWhenScreenIsLocked: false});
```
