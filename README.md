cordova-imagePicker
===================

Fork of Cordova Plugin For Multiple Image Selection - implemented for iOS and Android 4.0 and above.

```

### Options

    options = {
        // Android only. Max images to be selected, defaults to 15. If this is set to 1, upon
        // selection of a single image, the plugin will return it.
        maximumImagesCount: int,
        
        // max width and height to allow the images to be.  Will keep aspect
        // ratio no matter what.  So if both are 800, the returned image
        // will be at most 800 pixels wide and 800 pixels tall.  If the width is
        // 800 and height 0 the image will be 800 pixels wide if the source
        // is at least that wide.
        width: int,
        height: int,
        
        // quality of resized image, defaults to 100
        quality: int (0-100),

        // output type, defaults to FILE_URIs.
        // available options are 
        // window.imagePicker.OutputType.FILE_URI (0) or 
        // window.imagePicker.OutputType.BASE64_STRING (1)
        outputType: int
    };
    
### Note for Android Use

When outputType is FILE_URI the plugin returns images that are stored in a temporary directory.  These images will often not be deleted automatically though.  The files should be moved or deleted after you get their filepaths in javascript. If Base64 Strings are being returned, there is nothing to clean up.

## Android 6 (M) Permissions
On Android 6 you need to request permission to read external storage at runtime when targeting API level 23+.
Even if the `uses-permission` tags for the Calendar are present in `AndroidManifest.xml`.

Note that the `hasReadPermission` function will return true when:

- You're running this on iOS, or
- You're targeting an API level lower than 23, or
- You're using Android < 6, or
- You've already granted permission.

```js
  function hasReadPermission() {
    window.imagePicker.hasReadPermission(

