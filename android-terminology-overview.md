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
DP and DIP are actually the same thing and can be used interchangeably. They stand for Density Independent Pixels. This is one of the most useful measurements for designing across multiple screen densities and having everything lay out properly. Density independent pixels scale views so they lay out proportionally across various pixel densities. On a screen with a pixel density of 160dpi, 1dp is the same as 1px. As the pixel density increases for  higher resolution display, the ratio of dp to px will change. If you use dp/dip as the unit of measure, Android will decide the correct ratio for you so the views stay proportianal.  

### SP  
```
<TextView
  android:textSize="18sp" />
```
SP stands for Scale Independent Pixels. SP is very similar to DP/DIP, with only one main difference. Scale independent pixels adjust based on pixel density and user preference. This means if the user is visually impaired and specifies Large Text in their settings, sp will scale appropriately on their device. It is mainly used on text, but it can also be used on views containing text to ensure they expand to fit the text properly. If there are no custom settings specified on the user's device, sp behaves exactly the same as dp/dip.  

### PT
