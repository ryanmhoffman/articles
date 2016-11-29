# Android Animation Library  
The purpose of the library is to make animation in Android as easy as possible. The most you should have to do is pass in the app Context and the View you want to animate and call the correct method, i.e. ```slideInFromRight()``` or ```slideOutToBottom()``` and it should be no more complex than that if you don't want it to be.  

Android animations have come a long way through the years, especially since the introduction of Material Design with Lollipop. Since then Google have put an emphasis on meaningful animation to delight the users. With the release of Lollipop they drastically changed the framework for building animations to make it much easier to animate views and scenes. They also introduced a transition framework to make it possible to animate views across Activities and Fragments. That way any views that are shared can be easily animated through the transition without the need to disappear and be completely redrawn.

## Original Implementation  
The initial version requires you to create a new AndroidAnimation object using the constructor and then call the different methods on the object and pass in the View as a parameter in the method. Here is an example for animating a floating action button into place when the activity is created.
```
// Create the object in memory
private AndroidAnimation animation;
private FloatingActionButton fab;

@Override
protected void onCreate(Bundle savedInstanceState){
  super.onCreate(savedInstanceState);
  setContentView(R.id.my_awesome_layout);
  
  fab = (FloatingActionButton) findViewById(R.id.my_fab);
  
  // Initialize the AndroidAnimation object with app context.
  animation = new AndroidAnimation(this);
  
  // Animate the fab into view by sliding it up from the bottom of the screen
  animation.slideInFromBottom(fab);
  
  // Animate the fab out of view by sliding it down to the bottom of the screen
  animation.slideOutToBottom(fab);
}
```

## Current Implementation  
I have already made some changes to the library to make it so you won't have to initialize the object in your code. This means you won't have to hold a reference to it in memory. It looks like this:
```
private FloatingActionButton fab;

@Override
protected void onCreate(Bundle savedInstanceState){
  super.onCreate(savedInstanceState);
  setContentView(R.id.my_awesome_layout);
  
  fab = (FloatingActionButton) findViewById(R.id.my_fab);
  
  // Animate the fab into view by sliding it up from the bottom of the screen
  AndroidAnimation.with(this).slideInFromBottom(fab);
  
  // Animate the fab out of view by sliding it down to the bottom of the screen
  AndroidAnimation.with(this).setInvisible().slideOutToBottom(fab);
}
```
Handling the animation this way not only turns 3 lines of code into only a single line, but it also means you won't have to create an object and hold it in memory. The ```AndroidAnimation``` object does get returned in this version, but it can be garbage collected immediately since there will not be a reference to the object in memory after the animation is complete.
