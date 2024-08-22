# Background Processing

1. Q: Why is background processing important in Android?
   A: Background processing allows apps to perform operations without blocking the main thread, ensuring a responsive user interface and enabling work to continue even when the app is not in the foreground.

2. Q: What is the main thread in Android?
   A: The main thread, also known as the UI thread, is responsible for handling UI operations and user interactions. It's important to keep this thread free from long-running operations to maintain app responsiveness.

3. Q: What is an AsyncTask?
   A: AsyncTask is a helper class around Thread and Handler designed to run short operations in the background and publish results on the UI thread. However, it's deprecated as of Android 11.

4. Q: What are the limitations of AsyncTask?
   A: AsyncTask has several limitations: it's tied to the Activity lifecycle, can lead to memory leaks, doesn't handle configuration changes well, and is not suitable for long-running operations.

5. Q: What is a Handler in Android?
   A: A Handler allows you to send and process Message and Runnable objects associated with a thread's MessageQueue. It's often used to schedule actions to be executed at some point in the future.

6. Q: What is a Looper?
   A: A Looper is an Android class used to run a message loop for a thread. Loopers are used to implement event-driven programming in Android.

7. Q: What are Coroutines in Kotlin?
   A: Coroutines are a Kotlin feature for asynchronous programming. They allow you to write asynchronous code in a sequential manner, making it easier to manage background tasks.

8. Q: How do you start a coroutine in Android?
   A: You can start a coroutine using a CoroutineScope:
   ```kotlin
   lifecycleScope.launch {
       // Coroutine code here
   }
   ```

9. Q: What is WorkManager?
   A: WorkManager is part of Android Jetpack and provides a unified API for deferrable background work that needs a guarantee to run, even if the app exits or the device restarts.

10. Q: How do you define a Worker for WorkManager?
    A: You define a Worker by extending the Worker class and implementing the doWork() method:
    ```kotlin
    class MyWorker(context: Context, params: WorkerParameters) : Worker(context, params) {
        override fun doWork(): Result {
            // Do the work here
            return Result.success()
        }
    }
    ```

11. Q: What is the difference between oneTimeWorkRequest and periodicWorkRequest in WorkManager?
    A: oneTimeWorkRequest is used for tasks that should be executed once, while periodicWorkRequest is used for tasks that need to be repeated at regular intervals.

12. Q: What is an IntentService?
    A: IntentService is a base class for Services that handle asynchronous requests expressed as Intents. It's deprecated as of Android 11 in favor of WorkManager.

13. Q: What is the JobScheduler API?
    A: JobScheduler is a system service that schedules jobs to be executed in your app's process. It's designed for tasks that don't need to run immediately and can benefit from batching.

14. Q: How does Doze mode affect background processing?
    A: Doze mode restricts background processes to save battery. It defers background CPU and network activity for apps when the device is unused for long periods.

15. Q: What is the purpose of the @WorkerThread annotation?
    A: The @WorkerThread annotation indicates that a method should only be called on a worker thread. It's used to catch accidental invocations on the main thread.

16. Q: How can you run a task periodically in the background?
    A: You can use WorkManager's PeriodicWorkRequest for this purpose:
    ```kotlin
    val periodicWork = PeriodicWorkRequestBuilder<MyWorker>(15, TimeUnit.MINUTES)
        .build()
    WorkManager.getInstance(context).enqueue(periodicWork)
    ```

17. Q: What is a ForegroundService?
    A: A ForegroundService is a service that performs a task noticeable to the user, must display a notification, and continues running even when the user is not interacting with the app.

18. Q: How do you start a ForegroundService?
    A: You start a ForegroundService by calling startForegroundService() and then calling startForeground() within the service:
    ```kotlin
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        context.startForegroundService(Intent(context, MyForegroundService::class.java))
    } else {
        context.startService(Intent(context, MyForegroundService::class.java))
    }
    ```

19. Q: What is the difference between launch and async in Kotlin coroutines?
    A: launch is used to start a coroutine that doesn't return a result, while async is used when you need to return a result from the coroutine.

20. Q: How can you cancel a running coroutine?
    A: You can cancel a coroutine by calling cancel() on its Job:
    ```kotlin
    val job = launch {
        // Coroutine code
    }
    job.cancel()
    ```
