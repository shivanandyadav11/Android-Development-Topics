# Intents and Intent Filters

1. Q: What is an Intent in Android?
   A: An Intent is a messaging object used to request an action from another app component. It can be used to start activities, services, or broadcast messages to receivers.

2. Q: What are the two types of Intents?
   A: The two types of Intents are Explicit Intents and Implicit Intents.

3. Q: What is an Explicit Intent?
   A: An Explicit Intent specifies the exact component (like an Activity) to start by name. It's typically used for communicating within your own app.

4. Q: What is an Implicit Intent?
   A: An Implicit Intent doesn't specify a particular component but declares a general action to perform. The system then finds the appropriate component to handle the intent.

5. Q: How do you create an Explicit Intent?
   A: You can create an Explicit Intent by specifying the context and the exact class of the component to start, like this:
   ```kotlin
   val intent = Intent(this, SecondActivity::class.java)
   startActivity(intent)
   ```

6. Q: What is an Intent Filter?
   A: An Intent Filter is a way for Android components (like Activities) to declare what types of Intents they can respond to. It's defined in the AndroidManifest.xml file.

7. Q: How do you define an Intent Filter?
   A: You define an Intent Filter in the AndroidManifest.xml file using the `<intent-filter>` element within a component's declaration.

8. Q: What are the main elements of an Intent Filter?
   A: The main elements of an Intent Filter are `<action>`, `<category>`, and `<data>`.

9. Q: How can you pass data between Activities using Intents?
   A: You can use the putExtra() method to add data to an Intent, and then retrieve it in the receiving Activity using getIntent().getXXXExtra() methods.

10. Q: What is the difference between startActivity() and startActivityForResult()?
    A: startActivity() is used to start a new activity without expecting a result back, while startActivityForResult() is used when you expect a result from the started activity.

11. Q: What is a PendingIntent?
    A: A PendingIntent is a token that you give to another application (e.g., NotificationManager, AlarmManager) which allows the other application to use your application's permissions to execute a predefined piece of code.

12. Q: How do you create a broadcast Intent?
    A: You can create a broadcast Intent by using the Intent constructor and then calling sendBroadcast(), sendOrderedBroadcast(), or sendStickyBroadcast().

13. Q: What is the purpose of the FLAG_ACTIVITY_NEW_TASK flag?
    A: The FLAG_ACTIVITY_NEW_TASK flag is used to start an Activity in a new task. It's often used when starting an Activity from outside of an Activity context.

14. Q: How can you get the result from an Activity started with startActivityForResult()?
    A: You can override the onActivityResult() method in your calling Activity to receive and handle the result.

15. Q: What is the difference between an ordered and an unordered broadcast?
    A: An ordered broadcast is sent to receivers one at a time, which allows each receiver to propagate results to the next receiver. An unordered broadcast is sent to all receivers at roughly the same time.

16. Q: What is the purpose of the Intent.ACTION_MAIN action?
    A: The Intent.ACTION_MAIN action indicates that this Activity is the entry point of the application. It's typically used with CATEGORY_LAUNCHER to place the Activity in the system's app launcher.

17. Q: How can you prevent other apps from starting your Activity?
    A: You can set the exported attribute to false in your Activity's manifest declaration to prevent other apps from starting your Activity.

18. Q: What is Intent resolution?
    A: Intent resolution is the process by which the Android system determines which components can respond to an implicit Intent by comparing it against the Intent Filters declared in the manifest files of installed apps.

19. Q: What is the difference between Bundle and Intent?
    A: A Bundle is a mapping from String keys to various Parcelable types, used to pass data between components. An Intent is a messaging object used to request an action from another app component, which can include a Bundle of extra data.

20. Q: How can you use Intents to open a web page in a browser?
    A: You can create an Intent with ACTION_VIEW and set the data to a Uri object containing the URL:
    ```kotlin
    val intent = Intent(Intent.ACTION_VIEW, Uri.parse("https://www.example.com"))
    startActivity(intent)
    ```
