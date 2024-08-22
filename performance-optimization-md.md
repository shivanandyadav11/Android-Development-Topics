# Performance Optimization

1. Q: What is ANR in Android?
   A: ANR stands for "Application Not Responding." It occurs when an app cannot respond to user input within a reasonable time, typically 5 seconds for a background service or broadcast receiver, and about 20 seconds for an activity.

2. Q: How can you prevent ANRs?
   A: To prevent ANRs:
   - Avoid long operations on the main thread
   - Use AsyncTask, Handlers, or Coroutines for background operations
   - Optimize your code to reduce processing time
   - Use StrictMode to detect accidental disk or network access on the main thread

3. Q: What is the Android Profiler?
   A: The Android Profiler is a tool in Android Studio that provides real-time data to help you understand how your app uses CPU, memory, network, and battery resources.

4. Q: How can you reduce battery consumption in your app?
   A: To reduce battery consumption:
   - Minimize wake locks
   - Batch network requests
   - Use JobScheduler for background tasks
   - Optimize location requests
   - Use power-efficient APIs like WorkManager

5. Q: What is memory leak in Android?
   A: A memory leak occurs when your program keeps holding references to objects that are no longer needed, preventing the garbage collector from reclaiming memory.

6. Q: How can you detect and fix memory leaks?
   A: You can detect memory leaks using:
   - Android Studio's Memory Profiler
   - LeakCanary library
   To fix memory leaks:
   - Avoid strong references to Activities, Fragments, or Views in long-lived objects
   - Use WeakReferences where appropriate
   - Unregister listeners and callbacks
   - Be cautious with static variables

7. Q: What is the importance of ViewHolder pattern in ListView/RecyclerView?
   A: The ViewHolder pattern improves performance by caching view references, reducing the number of findViewById() calls, which are expensive operations.

8. Q: How can you optimize layouts for better performance?
   A: To optimize layouts:
   - Use ConstraintLayout to create flat view hierarchies
   - Avoid nested weights in LinearLayouts
   - Use <merge> tags to remove unnecessary view groups
   - Use <include> to reuse layouts
   - Use ViewStub for conditionally loaded views

9. Q: What is overdraw and how can you reduce it?
   A: Overdraw occurs when the same pixel is drawn multiple times in a single frame. To reduce overdraw:
   - Remove unnecessary backgrounds
   - Use custom drawables with smaller regions
   - Flatten your view hierarchy
   - Use clipRect() to reduce the draw area

10. Q: How can you optimize network usage in your app?
    A: To optimize network usage:
    - Batch network requests
    - Use efficient data formats like Protocol Buffers
    - Implement caching
    - Compress data
    - Use lazy loading for images and other content

11. Q: What is the purpose of ProGuard in Android?
    A: ProGuard is a tool that shrinks, optimizes, and obfuscates your code. It removes unused code and renames classes, fields, and methods with obscure names, making the APK smaller and harder to reverse engineer.

12. Q: How can you reduce APK size?
    A: To reduce APK size:
    - Enable ProGuard
    - Use Android App Bundle
    - Remove unused resources
    - Use vector drawables instead of multiple PNG files
    - Compress images
    - Use dynamic delivery for features or languages

13. Q: What is the importance of using appropriate data structures in Android?
    A: Using appropriate data structures can significantly impact performance. For example, using ArrayMap or SparseArray instead of HashMap can be more memory efficient for small sets.

14. Q: How can you optimize database operations?
    A: To optimize database operations:
    - Use indexes for frequently queried columns
    - Write efficient queries (avoid "SELECT *")
    - Use transactions for multiple operations
    - Consider using Room for better abstraction and optimization

15. Q: What is the purpose of StrictMode in Android?
    A: StrictMode is a developer tool that detects things you might be doing by accident and brings them to your attention so you can fix them. It can help detect disk reads, network access, or long operations on the main thread.

16. Q: How can you optimize the rendering performance of your UI?
    A: To optimize UI rendering:
    - Flatten your view hierarchy
    - Use hardware acceleration
    - Avoid overdraw
    - Use appropriate layouts (ConstraintLayout for complex UIs)
    - Implement view holding in RecyclerViews

17. Q: What is the importance of handling configuration changes efficiently?
    A: Efficient handling of configuration changes (like screen rotation) can improve user experience and prevent unnecessary resource consumption. Use ViewModel to retain data across configuration changes.

18. Q: How can you optimize the launch time of your app?
    A: To optimize launch time:
    - Minimize initialization in Application class
    - Use lazy initialization
    - Optimize your layout inflation
    - Use AsyncLayoutInflater for complex views
    - Consider using Splash screens

19. Q: What is the purpose of TraceView in Android?
    A: TraceView is a profiling tool that gives you a graphical representation of trace logs, including method trace data to help you debug your app and optimize its performance.

20. Q: How can you optimize power consumption in your app?
    A: To optimize power consumption:
    - Minimize wake locks
    - Batch and defer CPU-intensive tasks
    - Optimize location and sensor usage
    - Minimize network usage
    - Use JobScheduler or WorkManager for background tasks
    - Implement Doze mode and App Standby optimizations
