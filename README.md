# KAlert Dialog [![API](https://img.shields.io/badge/API-21%2B-brightgreen.svg?style=flat)](https://android-arsenal.com/api?level=21) [![JitPack](https://jitpack.io/v/moisoni97/KAlertDialog.svg)](https://jitpack.io/#moisoni97/KAlertDialog)
A beautiful and material alert dialog library for Android.

![image preview](https://github.com/moisoni97/KAlertDialog/blob/master/art/2.png)
![image preview](https://github.com/moisoni97/KAlertDialog/blob/master/art/4.png)
![image preview](https://github.com/moisoni97/KAlertDialog/blob/master/art/7.png)

# Getting Started

* You project should build against Android 5.0 (minSdkVersion 21).

* Add the JitPack repository to your project's build.gradle file:

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

* Add the dependency in your app's build.gradle file:

```gradle
dependencies {
    implementation 'com.github.moisoni97:KAlertDialog:1.0.0'
}
```

# Usage

* Show a basic message:

```java
new KAlertDialog(this)
        .setTitleText("Here's a message!")
        .show();
```	
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/1.png)

* Show a title with text under:

```java
new KAlertDialog(this)
        .setTitleText("Here's a message!")
        .setContentText("It's pretty, isn't it?")
        .show();
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/2.png)

* Show a title with gravity changed：

```java
new KAlertDialog(this, KAlertDialog.NORMAL_TYPE)
        .setTitleText("Lorem Ipsum")
        .setTitleTextGravity(Gravity.START)
        .setContentText("Lorem Ipsum is simply dummy text of the printing and typesetting industry.")
        .setConfirmClickListener("OK", null)
        .show();
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/3.png)

* Show a success message：

```java
new KAlertDialog(this, KAlertDialog.SUCCESS_TYPE)
        .setTitleText("Good job!")
        .setContentText("You clicked the button!")
        .show();
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/4.png)

* Show an error message：

```java
new KAlertDialog(this, KAlertDialog.ERROR_TYPE)
        .setTitleText("Oops...")
        .setContentText("Something went wrong!")
        .show();
```

* Show a warning message：

```java
 new KAlertDialog(this, KAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("You won't be able to recover this file!")
        .setConfirmClickListener("Yes, delete it!", null)
        .show();
```

* Show a message with a progress circle:

```java
KAlertDialog pDialog = new KAlertDialog(this, KAlertDialog.PROGRESS_TYPE);
    pDialog.getProgressHelper().setBarColor(Color.parseColor("#A5DC86"));
    pDialog.setTitleText("Loading");
    pDialog.setCancelable(false);
    pDialog.show();
```

* Show a message with a custom icon：

```java
new KAlertDialog(this, KAlertDialog.CUSTOM_IMAGE_TYPE)
        .setTitleText("Sweet!")
        .setContentText("Here's a custom image.")
        .setCustomImage(R.drawable.custom_img)
        .show();
```	

* Show a message with a custom vector drawable with tint option for night mode: 

```java
new KAlertDialog(this, KAlertDialog.CUSTOM_IMAGE_TYPE)
        .setTitleText("Sweet!")
        .setContentText("Here's a custom image.")
        .setCustomImage(R.drawable.vector_drawable)
        .setDrawableTintOnNightMode(true, R.color.red) //will work only if your app is running in night mode
        .show();
```	

* Show a message with a custom image URL

```java
displayType - KAlertDialog.IMAGE_BIG - For full size image
displayType - KAlertDialog.IMAGE_CIRCLE - For circle crop image

new KAlertDialog(this, KAlertDialog.URL_IMAGE_TYPE)
        .setTitleText("KAlertDialog")
        .setContentText("Here's a custom image.")
        .setURLImage("image_url", displayType)
        .setConfirmClickListener("OK", null)
        .show();
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/5.png)

* Show a dialog with an input field

```java
KAlertDialog dialog = new KAlertDialog(this, KAlertDialog.INPUT_TYPE);
    dialog.setInputFieldHint("Write message");
    dialog.setTitleText("Edit Text");
    dialog.setConfirmClickListener("OK", kAlertDialog -> {
        kAlertDialog.dismissWithAnimation();
        kAlertDialog.getInputText(); //get the input text
        Toast.makeText(this, kAlertDialog.getInputText(), Toast.LENGTH_SHORT).show();
    });
    dialog.show();
    
    //this line is necessary to show keyboard when using input-field
    dialog.getWindow().clearFlags(WindowManager.LayoutParams.FLAG_NOT_FOCUSABLE
            |WindowManager.LayoutParams.FLAG_ALT_FOCUSABLE_IM);
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/6.png)

* Hide cancel and confirm button：

```java
new KAlertDialog(this, KAlertDialog.CUSTOM_IMAGE_TYPE)
        .setTitleText("Sweet!")
        .setContentText("Here's a custom image.")
        .setCustomImage(R.drawable.custom_img)
        .showConfirmButton(false) //hide confirm button
        .showCancelButton(false) //hide cancel button
        .show();
```   

* Use a custom font：
 - *To apply a custom font you can add it either under `assets/fonts` folder or `res/font` folder.*

```java
new KAlertDialog(this, KAlertDialog.NORMAL_TYPE)
        .setTitleText("Lorem Ipsum")
        .setTitleFontAssets("fonts/sf.ttf") //for font under `assets/fonts` folder
	.setContentFont(R.font.sf) //for font under `res/font` folder
        .setContentText("Lorem Ipsum is simply dummy text of the printing and typesetting industry.")
	.setConfirmButtonFont(R.font.sf)
	.setCancelButtonFontAssets("fonts/sf.ttf")
        .setConfirmClickListener("OK", null)
        .show();
```
![](https://github.com/moisoni97/KAlertDialog/blob/master/art/7.png)

* Change the title and content color:

```java
 .setTitleColor(R.color.yourColorName)
 .setContentColor(R.color.yourColorName)
```

* Change the content text alignment:

```java
 .setContentTextAlignment(View.TEXT_ALIGNMENT_VIEW_START, Gravity.START)
 .setContentTextAlignment(View.TEXT_ALIGNMENT_CENTER, Gravity.CENTER)   
```

* Bind the listener to confirm button：

```java
new KAlertDialog(this, KAlertDialog.WARNING_TYPE, 0)
        .setTitleText("Are you sure?")
        .setContentText("You won't be able to recover this file!")
        .setConfirmClickListener("Yes, delete it!",new KAlertDialog.KAlertClickListener() {
            @Override
            public void onClick(KAlertDialog sDialog) {
                sDialog.dismissWithAnimation();
            }
        })
        .show();
```

* Show the cancel button and bind listener：

```java
new KAlertDialog(this, KAlertDialog.WARNING_TYPE, 0)
        .setTitleText("Are you sure?")
        .setContentText("You won't be able to recover this file!")
        .setConfirmClickListener("Yes, delete it!", null)
        .showCancelButton(true)
        .setCancelClickListener("No, cancel!", new KAlertDialog.KAlertClickListener() {
            @Override
            public void onClick(KAlertDialog sDialog) {
                sDialog.cancel();
            }
        })
        .show();
```

* Customizing the alert dialog:

```java
    //tint the vector drawable to a specific color in night mode
    .setDrawableTintOnNightMode(true, R.color.white)
    
    //spread the text evenly with justify-content
    //set the font params to 'null' or an empty string "" to use the default font
    .justifyContentText("Content text", "red", "16px", "sf", ".ttf")

    //change confirm button color
    .confirmButtonColor(R.color.colorPrimary)

    //change cancel button color
    .cancelButtonColor(R.color.colorAccent) 

    //change the confirm button text color
    .setConfirmClickListener("OK", R.color.black, clickListener) 

    //change the cancel button text color
    .setCancelClickListener("CANCEL", R.color.black, clickListener)

    //change the text size
    .setContentTextSize(50) 

    //use html for title text and content text
    .setTitleText("<h2>Title</h2><br><p>Description here</p>")
```    

* Create a drawable file to chnage the button shape

```java
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true">
        <shape android:shape="rectangle">
            <solid android:color="#FF5474" />
            <corners android:radius="6dp" />
        </shape>
    </item>
    <item>
        <shape android:shape="rectangle">
            <solid android:color="#FF1744" />
            <corners android:radius="6dp" />
        </shape>
    </item>
</selector>

.confirmButtonColor(R.drawable.button_background) //apply the drawable file
```        

* Change the dialog style upon confirming：

```java
new KAlertDialog(this, KAlertDialog.WARNING_TYPE, 0)
        .setTitleText("Are you sure?")
        .setContentText("You won't be able to recover this file!")
        .setConfirmText("Yes, delete it!")
        .setConfirmClickListener(new KAlertDialog.KAlertClickListener() {
            @Override
            public void onClick(KAlertDialog sDialog) {
                sDialog
                    .setTitleText("Deleted!")
                    .setContentText("Your imaginary file has been deleted!")
                    .setConfirmClickListener("OK", null)
                    .changeAlertType(KAlertDialog.SUCCESS_TYPE);
            }
        })
        .show();
```

* Change or hide title and content text on alert type change:

```java
new KAlertDialog(this, KAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("You won't be able to recover this file!")
        .showCancelButton(true)
        .setCancelClickListener("No, cancel!", sDialog -> 
            sDialog.setTitleText(null)
                .setContentText("Your imaginary file is safe :)")
                .showCancelButton(false)
                .setConfirmClickListener("OK", null)
                .changeAlertType(KAlertDialog.ERROR_TYPE))
        .setConfirmClickListener("Yes, delete it!",sDialog -> 
            sDialog.setTitleText("Deleted!")
                .showCancelButton(false)
                .setContentText(null)
                .setConfirmClickListener("OK",null)
                .changeAlertType(KAlertDialog.SUCCESS_TYPE))
        .show();
```

# License

* [Apache Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

```
Copyright 2019 KAlertDialog

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

 http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.