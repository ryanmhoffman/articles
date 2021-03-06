# Android Unit of Measure Terminology  

Have you ever wondered why there are so many different units of measurement in the Android architecture? There is dp, dip, sp, px, pt, in and mm. Below I will run through what each one is and what their purpose is within the Android framework.

### PX  

```
<View
  android:layout_width:"50px"
  android:layout_height:"wrap_content" />
```  
In Android, px is short for pixels. It corresponds to actual pixels on the screen. In this example the view would be exactly 50 pixels wide. This is useful for getting your layout pixel perfect, but there is a catch when using px. The pixel density on the screen will vary across devices. The higher the pixel density is, the smaller the view will appear, even though it will still be 50px.  

### DP/DIP  

```
<View
  android:layout_width:"50dp"
  android:layout_height:"50dip" />
```
DP and DIP are actually the same thing and can be used interchangeably. They stand for Density Independent Pixels. This is one of the most useful measurements for designing across multiple screen densities and having everything lay out properly. Density independent pixels scale views so they lay out proportionally across various pixel densities. On a screen with a pixel density of 160dpi, 1dp is the same as 1px. As the pixel density increases for  higher resolution display, the ratio of dp to px will change. If you use dp/dip as the unit of measure, Android will decide the correct ratio for you so the views stay proportional across screens with various pixel densities. This is probably the most common unit used due to how easy it is to design across devices with minimal issues. It is worth noting that while dp and dip can be used interchangeably, dp is more commonly used because not only is it one less character to type, but it also corresponds with sp as you will see next.  

### SP  
```
<TextView
  android:textSize="18sp" />
```
SP stands for Scale Independent Pixels. SP is very similar to DP/DIP, with one main difference. Scale independent pixels adjust based on pixel density and user preference. This means if the user is visually impaired and specifies Large Text in their settings, sp will scale appropriately on their device. It is mainly used on text, but it can also be used on views containing text to ensure they expand to fit the text properly. If there are no custom settings specified on the user's device, sp will behave exactly the same as dp/dip.  

### PT  
```
<View
  android:layout_width:"25pt"
  android:layout_height:"35pt" />
```
PT is short for Point, and it is simply 1/72 of an inch. This assumes a screen with 72dpi (dots per inch.)  

### MM and IN  
```
<View
  android:layout_width:"1in"
  android:layout_height:"15mm" />
```
MM is the abbreviation for millimeters, and IN is the abbreviation for inches. These units refer to actual sizes and ignore factors like pixel density and screen size. Using a value like "1in" means the view will take up exactly 1 inch of screen real estate, and the same is true for millimeters.  

## Conclusion  
When designing layouts on Android, dp and sp are definitely the most commonly used units due to how easily they scale across different screens. It is always recommended that you test your layouts on as many different screen sizes as possible to ensure that everything is laid out as expected. Even with the units that scale across pixel densities there can still be inconsistencies, so never trust that your layout will look exactly like it does in the preview in Android Studio. 
