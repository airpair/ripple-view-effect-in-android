
Google is regularly updating its most popular mobile operating system Android. Last year, it released [Android Lollipop](https://www.android.com/versions/lollipop-5-0/ "Android 5.0") version with [lots of new features](http://tech.firstpost.com/news-analysis/android-5-0-lollipop-10-key-highlights-of-googles-latest-mobile-os-237917.html) and tons of APIs. 

However, each version of Android is born with some new and unique features, but Lollipop came up with some major advancements which were never seen in Android’s earlier versions (Gingerbread, Froyo, Jelly Bean, KitKat). One of the primary changes in Lollipop is the [material design](http://www.google.com/design/spec/material-design/introduction.html#introduction-principles) which has completely changed the look of android. This type of design has given an entire new design interface to Android 5.0 and introduced the new techniques of customizing the applications.

The primary goal of material design is to create an interface that works on all mobile devices and platforms. Material design also allows the third party app developers to develop their own custom application with elegant design effects. 

Material design includes various visual effects such as shrinking, rolling or expanding of UI elements on touch, 3D appearance of buttons, animated buttons, shadow effects, etc. These effects not only provide the attractive look to applications, but also creates a better user experience. 

If you are using Lollipop version in your smartphone, then you must have seen expanding or rolling effects in buttons on touch events. These effects are called Ripple Effects. It is the type of transition that happens when a user interacts with buttons. 

Demo Link: https://www.youtube.com/watch?v=LlKISmPbmgw 

In this tutorial you will learn how ripple effect can make your application attractive and how to develop it. 

## How to create Ripple View Effect 

As the emergence of material design in [Android Lollipop](http://theninehertz.com/detailed-comparision-of-android-lollipop-ios8), app developers have started to implement the various design effects in their Android applications. Among all the design effects ripple view effect gives the most elegant and exclusive look to an application. If you are also a mobile app developer and want to make your Android application more attractive by using ripple effect, then follow these 9 steps.

**1)** Firstly, create a new Android project in Eclipse by clicking on **File > New > Android Application Project**. 

**2)** Set the below string values to file *string.xml* placed under **res > values**. 
strings.xml

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
 <string name="app_name">RippleViewExample</string>
 <string name="hello_world">Hello world!</string>
 <string name="action_settings">Settings</string>
 <string name="click_me">Click Me</string>
</resources>
```
This file is used to save your time that could be consumed in [hardcoded values](https://en.wikipedia.org/wiki/Hard_coding). For example, let’s assume that a title string is used in every file of the application and after creating half of the files you want to make a slight change in title. Now, it will be very typical to make changes in all the files, but with String.xml file, the change needs to be done only at one place and that is in the xml file. 

**3)** Now find the *dimense.xml* file located under **res > values**, add the below values. 
dimens.xml

```
<resources>
  <!-- Default screen margins, per the Android Design guidelines.-->
 <dimen name="activity_horizontal_margin">16dp</dimen>
 <dimen name="activity_vertical_margin">16dp</dimen>
</resources>
```
This file is used to set the values of dimensions so that the application layout is adjusted automatically on each screen size. In this file you can specify various dimensions like padding, radius, width, text size etc. 

To set the dimensions, there are many units available such as pt (point), in (inches), px (pixels) but the preferred unit is dp ([density independent pixels](http://www.google.co.in/design/spec/layout/units-measurements.html#units-measurements-density-independent-pixels-dp-)) because dp adjust the layout of the application on the screen size of all densities. 

Previously, the popular approach was px (pixels), but it creates problems in the screens with different densities. For example, if the length of an element is 150px, then its size would be 1 inch on a medium density screen, whereas it would take only 0.5 inches on a high density screen, even if both screens has the same resolution. So, it is good to prefer “dp” which doesn’t create any type of screen problems and automatically adjust the element’s size.  


**4)** To set the color and shape of buttons, set the below values in *card_bk.xml* file located under **res > drawable**. 

cards_bk.xml
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
 <item android:left="1.2dp">
 <shape android:shape="rectangle"
 android:dither="true">
  <corners android:radius="2.9dp"/>
  <solid android:color="#ccc" />
  </shape>
 </item>
  <item android:bottom="1.6dp">
 <shape android:shape="rectangle"
  android:dither="true">
  <corners android:radius="3dp" />
 <solid android:color="@android:color/white" />
 </shape>
 </item>
</layer-list>
```
You can also choose different colors and shapes for buttons according to the background of your Android application.

**5)** Import the library [RippleView](https://github.com/siriscac/RippleView) in eclipse, which is located in the source code. It provides all the APIs that are necessary to create ripple effects in buttons.

**6)** Add this Ripple view library to your Android application by navigating **Properties > Android > Add > RippleView**. Click apply and then OK.

**7)** Now open the layout file (**ripple_view.xml**) and write the below code. This will create a simple layout with RippleViewButton.

ripple_view.xml
```
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:tools="http://schemas.android.com/tools"
 xmlns:ripple="http://schemas.android.com/apk/res/org.ninehertz.rippleview.sample"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:background="#d2d2d2"
 android:paddingBottom="@dimen/activity_vertical_margin"
 android:paddingLeft="@dimen/activity_horizontal_margin"
 android:paddingRight="@dimen/activity_horizontal_margin"
 android:paddingTop="@dimen/activity_vertical_margin"
 tools:context="org.ninehertz.rippleview.sample.RippleViewActivity" >
 
 <org.ninehertz.rippleviewlib.RippleView
 android:id="@+id/btn"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:layout_centerInParent="true"
 android:background="@drawable/card_bk"
 android:gravity="center"
 android:padding="35dp"
 android:text="@string/click_me"
 android:textAppearance="?android:attr/textAppearanceMedium"
 ripple:alphaFactor="0.7"
 ripple:hover="true"
 ripple:rippleColor="#58FAAC" />
 </RelativeLayout>
```
**8)** Make some changes in main activity class (**RippleViewActivity.java**). 
```
package org.ninehertz.rippleview.sample;
import android.app.Activity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Toast;
 
import org.ninehertz.rippleviewlib.RippleView;
 
public class RippleViewActivity extends Activity {
 
 RippleView mButton;
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.ripple_view);
 mButton = (RippleView) findViewById(R.id.btn);
 mButton.setOnClickListener(new View.OnClickListener() {
 
 @Override
 public void onClick(View v) {
 Toast.makeText(getApplicationContext(), "Ripples", Toast.LENGTH_LONG).show();
 }
 });
 }
 }

```

9) Run the project to see the ripple effect in button and you are good to go. Now you will be able to see a button with ripple effect view. 

##Benefits of using Ripple Effects in your Android application

- Gives the better usability and accessibility option 
- Provide new ways of user interaction that was not possible in older Android versions
- Gives the opportunities to customize the applications 
- Can be easily created by any third party app developer
- Compatible with multiple screen sizes
- Give a realistic and practical look to the buttons

##Conclusion

This was a very simple example of creating a button with ripple view effect. You can create any kind of ripple effect in your application by making some slight changes in the code. It is not a very typical task as you may think, just a little study and efforts can open the doors of success for creating smartphone apps with amazing ripple view effects.

If you like this tutorial then do not forget to share it with your friends on social media.