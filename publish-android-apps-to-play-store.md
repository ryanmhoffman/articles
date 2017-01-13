## How to Publish Android Apps to the Google Play Store  
Publishing an Android app is a relatively simple process, but outside of Google's own documentation there aren't a whole lot of resources on how to do it.  

### First Steps  
After you finish writing the code for your app, you need to go back through that code one more time to make sure you remove all of the code used for debugging. There are sure to be many logging calls and possibly extra methods and classes used for testing and debugging that are not necessary for release. These should be removed to decrease the size of the final apk. It is also important to check your gradle file to make sure you aren't importing any extra libraries that you don't use in your project. While you have the gradle file open, you will most likely want to enable ProGuard on your code. ProGuard is a tool that will go through all of your code, including any imported libraries you are using, and remove any classes or methods that are not used. This is the tool that will help you keep your method count under 64k, which is required by the Android platform. To enable ProGuard, look in the *release* buildType and add ```minifyEnabled true```. It should look something like this:

```
...
buildTypes {
  release {
    minifyEnabled true
    proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
  }
}
...
```  

After that you will need to open your manifest file and delete the attribute ```android:debuggable```. While in there you will want to double-check that you have set values for ```android:versionName``` and ```android:versionCode```. If it's not there, don't panic, these can also be set in your build.gradle file, and usually are. They would be set in the ```defaultConfig``` section. Once you are sure both of those values are set either in the manifest or with gradle, you are almost done with your code.  

The last thing you might need to update is your production server, if you are using one. If you were using test data from a test server, you will want to make sure all calls to the server are updated to your production server. Once that's updated you will probably need to test a few more times to make sure everything works as expected.  

### Build the Release apk  
Now that your code is completely ready for to go, it is time to build the app. The final build gets packaged into a .apk file extension. You can think of it as Android's equivalent to a .jar file. Android Studio makes it fairly simple to generate the final apk. The generated apk *must* be signed with your own certificate. It is also important to keep the key for this certificate, because without it, you will not be able to publish updates to your app. Do not store the key in a public place. That would allow anyone with access to the key to publish updates to your app as you, so you should be the only one with the key.  

#### Signing the App  
