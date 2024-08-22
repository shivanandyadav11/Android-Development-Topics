# Permissions

1. Q: What are permissions in Android?
   A: Permissions are restrictions that limit an app's access to certain system features or user data to protect the user's privacy and the device's security.

2. Q: What are the different types of permissions in Android?
   A: Android has three types of permissions:
   - Normal permissions
   - Dangerous permissions
   - Special permissions

3. Q: What's the difference between normal and dangerous permissions?
   A: Normal permissions are granted automatically at install time and don't pose much risk to user privacy. Dangerous permissions require explicit user approval and can potentially affect user privacy or device operation.

4. Q: How do you declare permissions in an Android app?
   A: You declare permissions in the AndroidManifest.xml file using the <uses-permission> tag:
   ```xml
   <uses-permission android:name="android.permission.CAMERA" />
   ```

5. Q: What is runtime permission?
   A: Runtime permission, introduced in Android 6.0 (API level 23), requires apps to request permission from the user at runtime before accessing sensitive resources, rather than at install time.

6. Q: How do you check if a permission is granted?
   A: You can check if a permission is granted using ContextCompat.checkSelfPermission():
   ```kotlin
   if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA) == PackageManager.PERMISSION_GRANTED) {
       // Permission is granted
   }
   ```

7. Q: How do you request a runtime permission?
   A: You can request a runtime permission using ActivityCompat.requestPermissions():
   ```kotlin
   ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.CAMERA), REQUEST_CODE)
   ```

8. Q: How do you handle the result of a permission request?
   A: You handle the result by overriding onRequestPermissionsResult():
   ```kotlin
   override fun onRequestPermissionsResult(requestCode: Int, permissions: Array<String>, grantResults: IntArray) {
       when (requestCode) {
           CAMERA_PERMISSION_CODE -> {
               if ((grantResults.isNotEmpty() && grantResults[0] == PackageManager.PERMISSION_GRANTED)) {
                   // Permission was granted
               } else {
                   // Permission denied
               }
               return
           }
       }
   }
   ```

9. Q: What is the purpose of the android:permission attribute?
   A: The android:permission attribute is used to restrict which applications can start a component (like an Activity or Service) or send a broadcast to a receiver.

10. Q: What are permission groups?
    A: Permission groups are collections of related permissions. When a user grants a dangerous permission, all other permissions in the same group are automatically granted.

11. Q: How can you check if you should show a rationale for requesting a permission?
    A: You can use ActivityCompat.shouldShowRequestPermissionRationale():
    ```kotlin
    if (ActivityCompat.shouldShowRequestPermissionRationale(this, Manifest.permission.CAMERA)) {
        // Show an explanation to the user
    }
    ```

12. Q: What is the WRITE_EXTERNAL_STORAGE permission used for?
    A: The WRITE_EXTERNAL_STORAGE permission is used to write to external storage (like SD card). Note that for Android 10 (API level 29) and above, this permission is not needed for app-specific directories.

13. Q: What are special permissions?
    A: Special permissions are particularly sensitive permissions that require the app to request them in the manifest and the user to explicitly grant them in the system settings.

14. Q: What is an example of a special permission?
    A: SYSTEM_ALERT_WINDOW is an example of a special permission. It allows an app to create windows that are shown on top of all other apps.

15. Q: How do you request a special permission?
    A: For special permissions, you typically need to direct the user to the system settings. For example, for SYSTEM_ALERT_WINDOW:
    ```kotlin
    if (!Settings.canDrawOverlays(this)) {
        val intent = Intent(Settings.ACTION_MANAGE_OVERLAY_PERMISSION, Uri.parse("package:$packageName"))
        startActivityForResult(intent, REQUEST_CODE)
    }
    ```

16. Q: What changes were made to permissions in Android 10 (API level 29)?
    A: Android 10 introduced scoped storage, which changes how apps can access files on external storage. It also added new location permissions like ACCESS_BACKGROUND_LOCATION.

17. Q: What is the difference between ACCESS_FINE_LOCATION and ACCESS_COARSE_LOCATION?
    A: ACCESS_FINE_LOCATION provides precise location (like GPS), while ACCESS_COARSE_LOCATION provides approximate location (like network-based).

18. Q: How can you revoke permissions for your app programmatically?
    A: You can revoke permissions using the revoke() method of the PackageManager:
    ```kotlin
    packageManager.revoke(packageName, Manifest.permission.CAMERA)
    ```

19. Q: What is the purpose of the READ_PHONE_STATE permission?
    A: The READ_PHONE_STATE permission allows an app to read phone state, including the phone number of the device, current cellular network information, the status of any ongoing calls, and a list of any PhoneAccounts registered on the device.

20. Q: How do you handle permissions in fragments?
    A: In fragments, you can use requestPermissions() similar to activities. However, you should override onRequestPermissionsResult() in both the fragment and its host activity, and call through to the fragment's implementation from the activity.
