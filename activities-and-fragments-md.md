# Activities and Fragments

1. Q: What is an Activity in Android?
   A: An Activity is a fundamental component of an Android app that represents a single screen with a user interface. It's responsible for creating the window in which UI components are placed.

2. Q: What is the lifecycle of an Activity?
   A: The Activity lifecycle consists of several callback methods: onCreate(), onStart(), onResume(), onPause(), onStop(), and onDestroy().

3. Q: What is the purpose of onCreate() method?
   A: The onCreate() method is called when the activity is first created. It's used to perform one-time initialization, such as creating views and binding data.

4. Q: What is a Fragment?
   A: A Fragment represents a portion of the user interface in an Activity. It's a modular section of an activity that has its own lifecycle and can be added or removed while the activity is running.

5. Q: What is the difference between startActivity() and startActivityForResult()?
   A: startActivity() is used to start a new activity without expecting a result back, while startActivityForResult() is used when you expect a result from the started activity.

6. Q: What is the purpose of onSaveInstanceState()?
   A: onSaveInstanceState() is called before an activity may be killed so that it can save its state. It's used to preserve the UI state across configuration changes or when the system kills and recreates the activity.

7. Q: What is a FragmentManager?
   A: FragmentManager is the class responsible for performing actions on your app's fragments, such as adding, removing, or replacing them, and adding them to the back stack.

8. Q: How do Fragments communicate with their host Activity?
   A: Fragments typically communicate with their host Activity through interfaces. The Fragment defines an interface, and the host Activity implements it.

9. Q: What is the difference between add() and replace() methods when dealing with Fragments?
   A: add() adds a fragment to the container without removing the existing fragments, while replace() removes the existing fragment(s) in the container before adding the new one.

10. Q: What is a DialogFragment?
    A: DialogFragment is a subclass of Fragment that can be used to display a floating dialog. It's a more flexible and reusable alternative to using the Dialog class directly.

11. Q: What is the purpose of setRetainInstance(true) in Fragments?
    A: setRetainInstance(true) allows a fragment to be retained across Activity re-creation (such as when rotating the screen). This can be useful for retaining expensive objects or long-running operations.

12. Q: What is the difference between Fragment and View?
    A: A Fragment is a self-contained component with its own lifecycle that can be reused across multiple activities, while a View is a UI widget that renders something on the screen and handles user interactions.

13. Q: What is a BackStack in Android?
    A: The BackStack is a stack of Fragment transactions that allows the user to reverse a fragment transaction (navigate backwards) by pressing the back button.

14. Q: What is the purpose of onAttach() method in a Fragment?
    A: onAttach() is called when the fragment is first attached to its context (usually an activity). It's often used to check if the activity implements required interfaces.

15. Q: What is a SingleTaskActivity?
    A: A SingleTaskActivity is an activity with a launchMode of "singleTask". It allows only one instance of the activity to exist at a time in the task stack.

16. Q: What is the difference between commitAllowingStateLoss() and commit() when dealing with FragmentTransactions?
    A: commitAllowingStateLoss() allows the commit to be executed after an activity's state has been saved, while commit() will throw an exception in this case.

17. Q: What is the purpose of onActivityResult() method?
    A: onActivityResult() is called when an activity you launched exits, giving you the requestCode you started it with, the resultCode it returned, and any additional data from it.

18. Q: What is a nested fragment?
    A: A nested fragment is a fragment that is placed inside another fragment, rather than directly in an activity.

19. Q: What is the purpose of addToBackStack() method when performing a FragmentTransaction?
    A: addToBackStack() adds the transaction to the back stack, allowing the user to reverse the transaction and "undo" the fragment operations using the Back button.

20. Q: What is the difference between FragmentPagerAdapter and FragmentStatePagerAdapter?
    A: FragmentPagerAdapter keeps every created Fragment in memory, while FragmentStatePagerAdapter destroys Fragments as the user navigates to other pages, minimizing memory usage.
