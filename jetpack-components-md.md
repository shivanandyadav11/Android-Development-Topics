# Jetpack Components

1. Q: What is Android Jetpack?
   A: Android Jetpack is a suite of libraries, tools, and guidance to help developers write high-quality apps more easily. It provides a set of components to help developers follow best practices, reduce boilerplate code, and write code that works consistently across Android versions and devices.

2. Q: What are the main categories of Jetpack components?
   A: The main categories of Jetpack components are:
   - Foundation
   - Architecture
   - Behavior
   - UI

3. Q: What is ViewModel in Android Jetpack?
   A: ViewModel is a class designed to store and manage UI-related data in a lifecycle conscious way. It allows data to survive configuration changes such as screen rotations.

4. Q: How do you create a ViewModel?
   A: You typically create a ViewModel by extending the ViewModel class and using a ViewModelProvider:
   ```kotlin
   class MyViewModel : ViewModel() {
       // ViewModel implementation
   }

   val viewModel: MyViewModel by viewModels()
   ```

5. Q: What is LiveData?
   A: LiveData is an observable data holder class that is lifecycle-aware. It allows you to build data objects that notify views when the underlying database changes.

6. Q: How do you use LiveData with ViewModel?
   A: You can use LiveData in a ViewModel like this:
   ```kotlin
   class MyViewModel : ViewModel() {
       private val _data = MutableLiveData<String>()
       val data: LiveData<String> = _data

       fun setData(newData: String) {
           _data.value = newData
       }
   }
   ```

7. Q: What is Data Binding?
   A: Data Binding is a support library that allows you to bind UI components in your layouts to data sources in your app using a declarative format rather than programmatically.

8. Q: How do you enable Data Binding in your project?
   A: You enable Data Binding in your module's build.gradle file:
   ```groovy
   android {
       ...
       buildFeatures {
           dataBinding true
       }
   }
   ```

9. Q: What is the Navigation component?
   A: The Navigation component is a framework for implementing navigation in an Android app. It provides a consistent API for navigating across your app and handles fragment transactions.

10. Q: How do you define a navigation graph?
    A: You define a navigation graph in an XML file in the res/navigation directory:
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <navigation xmlns:android="http://schemas.android.com/apk/res/android"
                xmlns:app="http://schemas.android.com/apk/res-auto"
                android:id="@+id/nav_graph"
                app:startDestination="@id/homeFragment">
        <fragment
            android:id="@+id/homeFragment"
            android:name="com.example.HomeFragment"
            android:label="Home">
            <action
                android:id="@+id/action_home_to_detail"
                app:destination="@id/detailFragment" />
        </fragment>
        <fragment
            android:id="@+id/detailFragment"
            android:name="com.example.DetailFragment"
            android:label="Detail" />
    </navigation>
    ```

11. Q: What is Room?
    A: Room is a part of Android Jetpack that provides an abstraction layer over SQLite to allow for more robust database access while harnessing the full power of SQLite.

12. Q: What are the main components of Room?
    A: The main components of Room are:
    - Database: Contains the database holder and serves as the main access point for the underlying connection to your app's persisted, relational data.
    - Entity: Represents a table within the database.
    - DAO: Contains the methods used for accessing the database.

13. Q: What is WorkManager?
    A: WorkManager is an API that makes it easy to schedule deferrable, asynchronous tasks that are expected to run even if the app exits or the device restarts.

14. Q: How do you define a Worker in WorkManager?
    A: You define a Worker by extending the Worker class:
    ```kotlin
    class MyWorker(context: Context, params: WorkerParameters) : Worker(context, params) {
        override fun doWork(): Result {
            // Perform the work here
            return Result.success()
        }
    }
    ```

15. Q: What is Paging in Android Jetpack?
    A: The Paging library helps you load and display small chunks of data at a time. Loading partial data on demand reduces usage of network bandwidth and system resources.

16. Q: What is the purpose of the Lifecycle component?
    A: The Lifecycle component allows you to build lifecycle-aware components that can adjust their behavior based on the current lifecycle state of an activity or fragment.

17. Q: What are Android KTX extensions?
    A: Android KTX is a set of Kotlin extensions that are part of Android Jetpack. These extensions provide concise, idiomatic Kotlin to existing Android APIs.

18. Q: What is the purpose of the CameraX library?
    A: CameraX is a Jetpack library that makes it easier to add camera capabilities to your app. It provides a consistent and easy-to-use API that works across most Android devices.

19. Q: What is Hilt?
    A: Hilt is a dependency injection library for Android that reduces the boilerplate of doing manual dependency injection in your project. It's built on top of the popular DI library Dagger to benefit from the compile-time correctness, runtime performance, scalability, and Android Studio support that Dagger provides.

20. Q: What is Compose in Android Jetpack?
    A: Jetpack Compose is Android's modern toolkit for building native UI. It simplifies and accelerates UI development on Android with less code, powerful tools, and intuitive Kotlin APIs.
