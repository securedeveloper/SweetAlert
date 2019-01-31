Sweet Alert Dialog
===================

This repo is a replica of [Sweet Alert by pedant](https://github.com/pedant/sweet-alert-dialog) which is no longer maintained and broken with latest versions.

The library is fixed with this cloned and ready to use.

If anybody finds any issue/request, feel free to open an issue.

SweetAlert for Android, a beautiful alert dialog for different purposes.


Inspired by JavaScript [SweetAlert](https://sweetalert.js.org/)

## ScreenShot
![image](/assets/change_type.gif)

## Setup
The simplest way to use SweetAlertDialog is to add the library as aar dependency to your build.

**Gradle**
In project build gradle file,

**Through jitpack**

```gradle
allprojects {
    repositories {
        //... other repositories ...
        maven { url "https://jitpack.io" }
    }
}
```
and in module build gradle file,

```
dependencies {
    implementation 'com.github.securedeveloper:sweet-alert:0.2.0'
}
```

## Usage

show material progress
```java
    SweetAlertDialog pDialog = new SweetAlertDialog(this, SweetAlertDialog.PROGRESS_TYPE);
    pDialog.getProgressHelper().setBarColor(Color.parseColor("#A5DC86"));
    pDialog.setTitleText("Loading");
    pDialog.setCancelable(false);
    pDialog.show();
```
![image](/assets/play_progress.gif)

You can customize progress bar dynamically with materialish-progress methods via 
```java
SweetAlertDialog.getProgressHelper()
    .resetCount()
    .isSpinning()
    .spin()
    .stopSpinning()
    .getProgress()
    .setProgress(float progress)
    .setInstantProgress(float progress)
    .getCircleRadius()
    .setCircleRadius(int circleRadius)
    .getBarWidth()
    .setBarWidth(int barWidth)
    .getBarColor()
    .setBarColor(int barColor)
    .getRimWidth()
    .setRimWidth(int rimWidth)
    .getRimColor()
    .setRimColor(int rimColor)
    .getSpinSpeed()
    .setSpinSpeed(float spinSpeed)
```
thanks to the project [materialish-progress](https://github.com/pnikosis/materialish-progress) and [@croccio](https://github.com/croccio) participation.

more usages about progress, please see the sample.

A basic message：
```java
    new SweetAlertDialog(this)
        .setTitleText("Here's a message!")
        .show();
```
A title with a text under：
```java
    new SweetAlertDialog(this)
        .setTitleText("Here's a message!")
        .setContentText("It's pretty, isn't it?")
        .show();
```
A error message：
```java
    new SweetAlertDialog(this, SweetAlertDialog.ERROR_TYPE)
        .setTitleText("Oops...")
        .setContentText("Something went wrong!")
        .show();
```
A warning message：
```java
    new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .show();
```
A success message：
```java
    new SweetAlertDialog(this, SweetAlertDialog.SUCCESS_TYPE)
        .setTitleText("Good job!")
        .setContentText("You clicked the button!")
        .show();
```
A message with a custom icon：
```java
    new SweetAlertDialog(this, SweetAlertDialog.CUSTOM_IMAGE_TYPE)
        .setTitleText("Sweet!")
        .setContentText("Here's a custom image.")
        .setCustomImage(R.drawable.custom_img)
        .show();
```
Bind the listener to confirm button：
```java
    new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .setConfirmClickListener(new SweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(SweetAlertDialog sDialog) {
                sDialog.dismissWithAnimation();
            }
        })
        .show();
```
Show the cancel button and bind listener to it：
```java
    new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setCancelText("No,cancel plx!")
        .setConfirmText("Yes,delete it!")
        .showCancelButton(true)
        .setCancelClickListener(new SweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(SweetAlertDialog sDialog) {
                sDialog.cancel();
            }
        })
        .show();
```
**Change** the dialog style upon confirming：
```java
    new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .setConfirmClickListener(new SweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(SweetAlertDialog sDialog) {
                sDialog
                    .setTitleText("Deleted!")
                    .setContentText("Your imaginary file has been deleted!")
                    .setConfirmText("OK")
                    .setConfirmClickListener(null)
                    .changeAlertType(SweetAlertDialog.SUCCESS_TYPE);
            }
        })
        .show();
```
