# Data Storage

1. Q: What are the main options for data storage in Android?
   A: The main options are Shared Preferences, Internal Storage, External Storage, SQLite Databases, Room Persistence Library, and Content Providers.

2. Q: What is SharedPreferences?
   A: SharedPreferences is a simple key-value storage system for saving primitive data types (boolean, float, int, long, and string) in Android.

3. Q: How do you write data to SharedPreferences?
   A: You can write data to SharedPreferences using an Editor object:
   ```kotlin
   val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
   val editor = sharedPref.edit()
   editor.putString("key", "value")
   editor.apply()
   ```

4. Q: What is the difference between apply() and commit() in SharedPreferences?
   A: apply() saves the changes asynchronously, while commit() saves synchronously and returns a boolean indicating success or failure.

5. Q: What is Internal Storage?
   A: Internal Storage is private storage space for your app that other apps cannot access. Files saved here are removed when the app is uninstalled.

6. Q: How do you write a file to Internal Storage?
   A: You can use openFileOutput() to get a FileOutputStream and write to it:
   ```kotlin
   val filename = "myfile"
   val fileContents = "Hello, World!"
   context.openFileOutput(filename, Context.MODE_PRIVATE).use {
       it.write(fileContents.toByteArray())
   }
   ```

7. Q: What is External Storage?
   A: External Storage is storage that's not always available (like an SD card). It's accessible by other apps and the user, but files can be read by any app.

8. Q: What permissions are needed to write to External Storage?
   A: For Android 9 (API level 28) and lower, you need the WRITE_EXTERNAL_STORAGE permission. For Android 10 (API level 29) and higher, you need to use scoped storage or the MANAGE_EXTERNAL_STORAGE permission.

9. Q: What is SQLite?
   A: SQLite is a lightweight, serverless, self-contained relational database engine that Android provides built-in support for.

10. Q: What is a ContentValues object used for in SQLite operations?
    A: A ContentValues object is used to store a set of values that the ContentResolver can process. It's commonly used when inserting or updating records in a SQLite database.

11. Q: What is the Room Persistence Library?
    A: Room is a part of Android Jetpack that provides an abstraction layer over SQLite to allow for more robust database access while harnessing the full power of SQLite.

12. Q: What are the main components of Room?
    A: The main components of Room are the Database, Entity, and DAO (Data Access Object).

13. Q: What is an Entity in Room?
    A: An Entity represents a table within the database. It's typically defined as a Kotlin data class annotated with @Entity.

14. Q: What is a DAO in Room?
    A: A DAO (Data Access Object) is an interface that defines the database operations you can perform. It's annotated with @Dao and contains methods for reading and writing data.

15. Q: How do you perform database migrations with Room?
    A: You define a Migration class that specifies how to convert database schemas from one version to another. You then add these Migration objects when building your database.

16. Q: What is a Content Provider?
    A: A Content Provider manages access to a central repository of data. It's used to share data between applications or with other components within the same app.

17. Q: What is the difference between Internal and External cache directories?
    A: The Internal cache directory is private to your app and is cleared when your app is uninstalled. The External cache directory can be accessed by other apps but may be cleared by the system when storage is low.

18. Q: How can you encrypt data stored in SharedPreferences?
    A: You can use the EncryptedSharedPreferences class from the Android Security library to encrypt both keys and values in SharedPreferences.

19. Q: What is the purpose of the .nomedia file?
    A: The .nomedia file, when placed in a directory, prevents media files in that directory from being indexed and showing up in gallery apps or music players.

20. Q: What is the difference between MODE_PRIVATE and MODE_WORLD_READABLE when creating files?
    A: MODE_PRIVATE creates a file that's only accessible by your app, while MODE_WORLD_READABLE (deprecated in API level 17) creates a file that's readable by any app. For security reasons, it's recommended to always use MODE_PRIVATE.
