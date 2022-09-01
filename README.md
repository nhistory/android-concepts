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

## 2. Common Layouts

A layout defines the structure for a user interface in your app, such as in an activity. All elements in the layout are built using a hierarchy of ```View``` and ```ViewGroup``` objects. A ```View``` usually draws something the user can see and interact with. Whereas a ```ViewGroup``` is an invisible container that defines the layout structure for ```View``` and other ```ViewGroup``` objects.[4]

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/184280448-1effcd3a-3bd4-465d-ab1d-7c7af817704d.png">

Each subclass of the ViewGroup class provides a unique way to display the views you nest within it. Below are some of the more common layout types that are built into the Android platform.

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/184282223-0079bfb8-05bd-4745-a611-3051802e8b52.png">

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/184282310-4db1c566-3484-4104-8bb1-78c931831757.png">

- [Linear Layout](https://developer.android.com/guide/topics/ui/layout/linear): A layout that organizes its children into a single horizontal or vertical row. It creates a scrollbar if the length of the window exceeds the length of the screen.
- [Relative Layout](https://developer.android.com/guide/topics/ui/layout/relative): Enables you to specify the location of child objects relative to each other (child A to the left of child B) or to the parent (aligned to the top of the parent).
- [Web View](https://developer.android.com/guide/webapps/webview): Displays web pages.
- [List View](https://developer.android.com/guide/topics/ui/layout/listview): Displays a scrolling single column list.
- [Grid View](https://developer.android.com/guide/topics/ui/layout/gridview): Displays a scrolling grid of columns and rows.

### Constraint layout

[ConstraintLayout](https://developer.android.com/training/constraint-layout) allows you to create large and complex layouts with a flat view hierarchy (no nested view groups). It's similar to RelativeLayout in that all views are laid out according to relationships between sibling views and the parent layout, but it's more flexible than RelativeLayout and easier to use with Android Studio's Layout Editor.

## 3. Add feature on button click

After make several `<EditText>`, we can get some data from user with button click. To doing this, each of EditText has their own id value. And then we can use input data from that EditText section. After enter any text into the input sections, you can find log on the `Logcat` window below.

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        btnApply.setOnClickListener{
            val firstName = etFirstName.text.toString()
            val lastName = etLastName.text.toString()
            val birthDate = etBirthDate.text.toString()
            val country = etCountry.text.toString()
            Log.d("MainActivity", "$firstName $lastName, born on $birthDate, from $country just applied to the formular.")
        }
    }
}
```

<img width="450" alt="image" src="https://user-images.githubusercontent.com/39740066/186049223-6307eaf8-7d08-4b15-8870-491eaed8f437.png">

<img width="600" alt="image" src="https://user-images.githubusercontent.com/39740066/186049122-d5f38ae1-6ceb-490e-a560-461132f430c8.png">

To import `btnApply` with `kotlinx.android.synthetic.main.activity_main.*`, you need to add `id 'kotlin-android-extensions'` on `gradle.build`.

## Android Context

What is Android context?

Definition. it's the context of current state of the application/object. It lets newly-created objects understand what has been going on. Typically, you call it to get information regarding another part of your program (activity and package/application).

If we want to move other activity, `Context` will help show up new xml file with activity. For example, `Intent` is a one of the context method to show what is the intention of next activity like below. 

```kotlin
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        btnOpenActivity.setOnClickListener {
            Intent(this, SecondActivity::class.java).also {
                startActivity(it)
            }
        }
    }
```

## References
* [1] https://developer.android.com/guide/components/activities/intro-activities
* [2] https://developer.android.com/guide/components/activities/tasks-and-back-stack
* [3] https://developer.android.com/reference/android/app/Activity#ActivityLifecycle
* [4] https://developer.android.com/guide/topics/ui/declaring-layout#kotlin
* [5] https://www.geeksforgeeks.org/what-is-context-in-android/
