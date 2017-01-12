## How to Publish Android Apps to the Google Play Store  
Publishing an Android app is a relatively simple process, but outside of Google's own documentation there aren't a whole lot of resources on how to do it.  

### First Steps  
After you finish writing the code for your app, you need to go back through that code one more time to make sure you remove all of the code used for debugging. There are sure to be many logging calls and possibly extra methods and classes used for testing and debugging that are not necessary for release. These should be removed to decrease the size of the final apk. It is also important to check your gradle file to make sure you aren't importing any extra libraries that you don't use in your project.  

After that you will need to open your manifest file and delete the attribute ```android:debuggable```. 
