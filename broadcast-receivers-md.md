# Broadcast Receivers

1. Q: What is a Broadcast Receiver in Android?
   A: A Broadcast Receiver is an Android component that allows you to register for system or application events. It responds to broadcast messages from various sources, including the Android system and other applications.

2. Q: How do you create a Broadcast Receiver?
   A: You can create a Broadcast Receiver by subclassing the BroadcastReceiver class and implementing the onReceive() method:
   ```kotlin
   class MyReceiver : BroadcastReceiver() {
       override fun onReceive(context: Context, intent: Intent) {
           // Handle received broadcast
       }
   }
   ```

3. Q: What are the two ways to register a Broadcast Receiver?
   A: You can register a Broadcast Receiver either statically in the AndroidManifest.xml file, or dynamically in your code using registerReceiver().

4. Q: How do you register a Broadcast Receiver in the AndroidManifest.xml?
   A: You can register a Broadcast Receiver in the AndroidManifest.xml like this:
   ```xml
   <receiver android:name=".MyReceiver">
       <intent-filter>
           <action android:name="android.intent.action.BOOT_COMPLETED"/>
       </intent-filter>
   </receiver>
   ```

5. Q: How do you register a Broadcast Receiver dynamically?
   A: You can register a Broadcast Receiver dynamically using registerReceiver():
   ```kotlin
   val filter = IntentFilter("com.example.MY_ACTION")
   registerReceiver(myReceiver, filter)
   ```

6. Q: What is the difference between normal broadcasts and ordered broadcasts?
   A: Normal broadcasts are sent to all registered receivers simultaneously, while ordered broadcasts are delivered to one receiver at a time in a specified order.

7. Q: How do you send a broadcast?
   A: You can send a broadcast using sendBroadcast():
   ```kotlin
   val intent = Intent("com.example.MY_ACTION")
   sendBroadcast(intent)
   ```

8. Q: What is a LocalBroadcastManager?
   A: LocalBroadcastManager is a class that allows you to register for and send broadcasts that are local to your application, improving efficiency and security.

9. Q: How do you use LocalBroadcastManager?
   A: You can use LocalBroadcastManager like this:
   ```kotlin
   LocalBroadcastManager.getInstance(this).registerReceiver(myReceiver, IntentFilter("MY_ACTION"))
   LocalBroadcastManager.getInstance(this).sendBroadcast(intent)
   ```

10. Q: What is the purpose of the sticky broadcast?
    A: A sticky broadcast is a broadcast that sticks around after it has been sent, so that components registering for it later can still receive it.

11. Q: How do you send an ordered broadcast?
    A: You can send an ordered broadcast using sendOrderedBroadcast():
    ```kotlin
    sendOrderedBroadcast(Intent("MY_ACTION"), null)
    ```

12. Q: What is the purpose of the BroadcastReceiver.PendingResult class?
    A: BroadcastReceiver.PendingResult allows a BroadcastReceiver to send results to the next receiver in an ordered broadcast.

13. Q: How can you abort a broadcast in an ordered broadcast?
    A: You can abort a broadcast in an ordered broadcast by calling abortBroadcast() in your onReceive() method.

14. Q: What are some common system broadcasts?
    A: Common system broadcasts include BOOT_COMPLETED, BATTERY_LOW, SCREEN_ON, SCREEN_OFF, and CONNECTIVITY_CHANGE.

15. Q: Are there any limitations on Broadcast Receivers in recent Android versions?
    A: Yes, starting from Android 8.0 (API level 26), there are limitations on implicit broadcasts to improve system performance and battery life. Many implicit broadcasts no longer work with manifest-declared receivers.

16. Q: How do you unregister a dynamically registered Broadcast Receiver?
    A: You can unregister a dynamically registered Broadcast Receiver using unregisterReceiver():
    ```kotlin
    unregisterReceiver(myReceiver)
    ```

17. Q: What is the context in which onReceive() method is executed?
    A: The onReceive() method is executed on the main thread, so it should complete quickly (under 10 seconds). Long-running operations should be scheduled for later execution.

18. Q: Can a Broadcast Receiver start an Activity?
    A: Yes, a Broadcast Receiver can start an Activity, but it's generally recommended to show notifications instead, especially for broadcasts sent by the system.

19. Q: What is the difference between sendBroadcast() and sendStickyBroadcast()?
    A: sendBroadcast() sends a standard broadcast that disappears after being handled, while sendStickyBroadcast() (deprecated in API level 21) sends a broadcast that remains accessible after the broadcast is complete.

20. Q: How can you make a Broadcast Receiver run on a specific thread?
    A: By default, a Broadcast Receiver runs on the main thread. To run it on a different thread, you can use goAsync() in your onReceive() method:
    ```kotlin
    override fun onReceive(context: Context, intent: Intent) {
        val pendingResult = goAsync()
        Thread(Runnable {
            // Do work here
            pendingResult.finish()
        }).start()
    }
    ```
