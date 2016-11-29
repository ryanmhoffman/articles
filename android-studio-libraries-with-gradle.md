# Using Libraries in Android Studio  

## Intro to Gradle for Android Studio

Android Studio switched to a gradle based build system a few years ago, and that made it very simple to incorporate open source libraries  your Android projects. If you aren't familiar with gradle you can learn more about it [here](https://gradle.org/getting-started-android-build/). The details of gradle recipes are beyond the scope of this post, but I will show the very basics of including libraries in your project. Fortunately gradle makes it dummy-proof to add dependencies in your project. Gradle is not the only way to add a library to your project, and if you are familiar with eclipse then you are most likely familiar with adding .jar files to your project. This is still possible in Android Studio, and I do cover how to do that below, but I don't recommend it. By using gradle, all you need to do is include 1 line of code in you ```build.gradle``` file and it does the rest. It pulls in the dependency at build time so it doesn't need to be downloaded and included as a .jar file. Even more appealing than that is how easy it is to use it with different versions of libraries. With gradle, if you are using ```my-awesome-library:v1-0``` but then version 2-0 comes out, all you have to do is change that statement to ```my-awesome-library:v2-0``` and start using the updates immediately. That is much easier than deleting the .jar and downloading and adding the new version.  

So now that we know the differences let's look at both ways, starting with gradle.  

## Adding Libraries with Gradle  

When you create a new project in Android Studio it is already preconfigured to use gradle. If you look through the project files that are created initially you will find a couple different gradle files. The first one is probably your high level project file. This is the gradle file to configure project-wide settings. We will not need to modify this file for what we are going to accomplish in this tutorial. Next will be the module level gradle files. If you created a simple app with only one module then there will only be one module level ```build.gradle```. If you included other modules in your project, for example Android Wear, Android TV, or Android Auto then there should be more than one version of this file for each module. Each one should be labeled next to it in parentheses describing what it is for. 
```
build.gradle (Project)
build.gradle (app)
build.gradle (wear)
```
The one you need to edit is the ```build.gradle (app)``` to add the open source library to our project. The library we are going to add in this example is Google's [CardView](https://developer.android.com/training/material/lists-cards.html#CardView) library.  

Here's how easy it is to add a library to your project with gradle and Android Studio. Start by opening the ```build.gradle``` file for the app module. Find the section near the bottom labeled ```dependencies``` and add this line to the bottom of that section: 
```
compile 'com.android.support:cardview-v7:25.0.0'
```
It should look like this:
```
dependencies {
  // other module dependencies may be listed here
  ...
  compile 'com.android.support:cardview-v7:25.0.0'
}
```
Once you add that line Android Studio will let you know that gradle files have changed and prompt you to sync your project with gradle. Once you do that you can immediatly begin using the library in your code. If a new version is released just change the version number in your gradle file and sync your project again and that's it.  

## Adding Libraries as .jar Files  
