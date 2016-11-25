# Android Animation Library  
The purpose of the library is to make animation in Android as easy as possible. The most you should have to do is pass in the app Context and the View you want to animate and call the correct method, i.e. ```slideInFromRight()``` or ```slideOutToBottom()``` and it should be no more complex than that if you don't want it to be. 

## Current Implementation  
The current version requires you to create a new AndroidAnimation object using the constructor and then call the different methods on the object and pass in the View as a parameter in the method. Here is an example for animating a floating action button into place when the activity is created.
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
  
  // Animate the fab into view by sliding it up from the bottom of the screen.
  animation.slideInFromBottom(fab);
}
```

## Next Idea For Implementation  
I plan to change the implementation to make it so you won't have to initialize the object in your code, which means you won't have to hold a reference to it in memory. It would look something like this:
```
private FloatingActionButton fab;

@Override
protected void onCreate(Bundle savedInstanceState){
  super.onCreate(savedInstanceState);
  setContentView(R.id.my_awesome_layout);
  
  fab = (FloatingActionButton) findViewById(R.id.my_fab);
  
  // Animate the fab into view by sliding it up from the bottom of the screen
  AndroidAnimation.with(this).slideInFromBottom(fab).animate();
}
```
Handling the animation this way not only turns 3 lines of code into only a single line, but it also means you won't have to create an object and hold it in memory. 
