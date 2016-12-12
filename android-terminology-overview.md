# Android Unit of Measure Terminology  

Have you ever wondered why there are so many different units of measurement in the Android architecture? You have dp, dip, sp, px, pt, in, mm, and the list could go on. Below I will run through the purpose of each and their most common use cases when designing layouts in Android.  

### PX  

```
<View
  android:layout_width:"50px"
  android:layout_height:"wrap_content" />
```  
In Android, px is short for pixels. It corresponds to actual pixels on the screen. In this example the view would be exactly 50 pixels wide. This is useful for getting your layout pixel perfect, but there is one very big pitfall to watch out for. The pixel density on the screen can vary across devices. The higher the pixel density is, the smaller the view will appear, even though it will still be 50px.  

### DP/DIP  

```
<View
  android:layout_width:"50dp"
  android:layout_height:"50dip" />
```
