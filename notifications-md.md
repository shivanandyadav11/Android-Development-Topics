# Notifications

1. Q: What is a Notification in Android?
   A: A Notification is a message that Android displays outside your app's UI to provide reminders, communication from other people, or other timely information from your app. Users can tap the notification to open your app or take an action directly from the notification.

2. Q: How do you create a basic Notification?
   A: To create a basic Notification:
   1. Get an instance of NotificationCompat.Builder
   2. Set the Notification content and channel
   3. Build the Notification
   4. Show the Notification using NotificationManagerCompat
   Example:
   ```kotlin
   val builder = NotificationCompat.Builder(context, CHANNEL_ID)
       .setSmallIcon(R.drawable.notification_icon)
       .setContentTitle("My notification")
       .setContentText("Much longer text that cannot fit one line...")
       .setPriority(NotificationCompat.PRIORITY_DEFAULT)
   
   NotificationManagerCompat.from(context).notify(notificationId, builder.build())
   ```

3. Q: What is a Notification Channel?
   A: A Notification Channel represents a type of notification that the app might send. It allows users to have fine-grained control over different kinds of notifications from an app. Channels are required for all notifications on Android 8.0 (API level 26) and above.

4. Q: How do you create a Notification Channel?
   A: To create a Notification Channel:
   ```kotlin
   if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
       val name = getString(R.string.channel_name)
       val descriptionText = getString(R.string.channel_description)
       val importance = NotificationManager.IMPORTANCE_DEFAULT
       val channel = NotificationChannel(CHANNEL_ID, name, importance).apply {
           description = descriptionText
       }
       val notificationManager: NotificationManager =
           getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager
       notificationManager.createNotificationChannel(channel)
   }
   ```

5. Q: What are the different Notification priorities?
   A: Notification priorities are:
   - PRIORITY_MIN: Min priority; only show in the shade, not in status bar
   - PRIORITY_LOW: Low priority; show in the shade, and potentially in the status bar
   - PRIORITY_DEFAULT: Default priority
   - PRIORITY_HIGH: Higher priority, for more important notifications
   - PRIORITY_MAX: Highest priority, for your application's most important items

6. Q: How do you add actions to a Notification?
   A: You can add actions to a Notification using the addAction() method:
   ```kotlin
   val intent = Intent(context, AlertDetails::class.java).apply {
       flags = Intent.FLAG_ACTIVITY_NEW_TASK or Intent.FLAG_ACTIVITY_CLEAR_TASK
   }
   val pendingIntent: PendingIntent = PendingIntent.getActivity(context, 0, intent, PendingIntent.FLAG_IMMUTABLE)

   val builder = NotificationCompat.Builder(context, CHANNEL_ID)
       .setSmallIcon(R.drawable.notification_icon)
       .setContentTitle("My notification")
       .setContentText("Hello World!")
       .setPriority(NotificationCompat.PRIORITY_DEFAULT)
       .addAction(R.drawable.ic_action, "Open", pendingIntent)
   ```

7. Q: What is a PendingIntent and why is it used with Notifications?
   A: A PendingIntent is a description of an Intent and target action to perform with it. It's used with notifications to specify an action to be performed when the notification is clicked or when a notification action button is pressed.

8. Q: How can you update an existing Notification?
   A: To update an existing Notification, use the same ID when calling notify():
   ```kotlin
   notificationManager.notify(notificationId, builder.build())
   ```

9. Q: How do you create a Notification with a large icon or image?
   A: You can set a large icon or image using setLargeIcon() and setStyle() methods:
   ```kotlin
   val bitmap = BitmapFactory.decodeResource(resources, R.drawable.large_icon)
   val builder = NotificationCompat.Builder(context, CHANNEL_ID)
       .setSmallIcon(R.drawable.notification_icon)
       .setLargeIcon(bitmap)
       .setStyle(NotificationCompat.BigPictureStyle()
           .bigPicture(bitmap)
           .bigLargeIcon(null))
   ```

10. Q: What is a Foreground Service Notification?
    A: A Foreground Service Notification is a notification that's shown when a service is running in the foreground. It's required for foreground services and can't be dismissed by the user while the service is running.

11. Q: How do you create a Foreground Service Notification?
    A: To create a Foreground Service Notification:
    ```kotlin
    val pendingIntent: PendingIntent =
        Intent(this, MainActivity::class.java).let { notificationIntent ->
            PendingIntent.getActivity(this, 0, notificationIntent, PendingIntent.FLAG_IMMUTABLE)
        }

    val notification: Notification = NotificationCompat.Builder(this, CHANNEL_ID)
        .setContentTitle("Foreground Service")
        .setContentText("Service is running")
        .setSmallIcon(R.drawable.notification_icon)
        .setContentIntent(pendingIntent)
        .build()

    startForeground(ONGOING_NOTIFICATION_ID, notification)
    ```

12. Q: What is a Heads-up Notification?
    A: A Heads-up Notification is a notification that appears in a small floating window at the top of the screen when the device is unlocked. It's typically used for high-priority notifications that require immediate attention.

13. Q: How do you create a Heads-up Notification?
    A: To create a Heads-up Notification, set the priority to HIGH or MAX and include a sound or vibration:
    ```kotlin
    val builder = NotificationCompat.Builder(context, CHANNEL_ID)
        .setSmallIcon(R.drawable.notification_icon)
        .setContentTitle("Urgent Notification")
        .setContentText("This is a heads-up notification!")
        .setPriority(NotificationCompat.PRIORITY_HIGH)
        .setVibrate(longArrayOf(0, 1000))
    ```

14. Q: How can you group multiple Notifications