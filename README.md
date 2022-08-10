# android-concepts

This repository is for learning and archiving main concepts and fundamentals of android development.

## 1. Activities

An activity provides the window in which the app draws its UI. This window typically fills the screen, but may be smaller than the screen and float on top of other windows. Generally, one activity implements one screen in an app.

When one app invokes another, the calling app invokes an activity in the other app, rather than the app as an atomic whole. In this way, the activity serves as the entry point for an app's interaction with the user. You implement an activity as a subclass of the Activity class.

Most apps contain multiple screens, which means they comprise multiple activities. Typically, one activity in an app is specified as the main activity, which is the first screen to appear when the user launches the app. Each activity can then start another activity in order to perform different actions.[1]

### Activity stack

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/183552121-1e9d30df-1179-4ceb-ae24-f35e439213be.png">

A task is a collection of activities that users interact with when trying to do something in your app. These activities are arranged in a stack—the back stack—in the order in which each activity is opened. For example, an email app might have one activity to show a list of new messages.[2]

### Activity lifecycle

```java
 public class Activity extends ApplicationContext {
     protected void onCreate(Bundle savedInstanceState);

     protected void onStart();

     protected void onRestart();

     protected void onResume();

     protected void onPause();

     protected void onStop();

     protected void onDestroy();
 }
```
<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/183553807-562e1045-964f-4f83-8acc-41b4c5b8390a.png">[3]

### Overide activity

In order to add new activities, press ```ctrl+o``` then you can see override members. For instance, if you enter `onpause` and press enter key, ```onPause()``` function would be inserted.

<img width="430" alt="image" src="https://user-images.githubusercontent.com/39740066/183558120-367e0773-99be-4f8c-a07b-af91de55befc.png">

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/183558156-2a6c8fff-aa60-46ed-aab5-50dccd77e56e.png">



## References
* [1] https://developer.android.com/guide/components/activities/intro-activities
* [2] https://developer.android.com/guide/components/activities/tasks-and-back-stack
* [3] https://developer.android.com/reference/android/app/Activity#ActivityLifecycle
