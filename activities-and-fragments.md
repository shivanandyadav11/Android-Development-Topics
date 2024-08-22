# 📱 Android Activities and Fragments: Q&A Cheat Sheet

## 🚀 Introduction

This cheat sheet provides a quick reference for key concepts related to Activities and Fragments in Android development. Presented in a Q&A format, it covers essential information for both beginners and experienced developers working with these fundamental components of Android apps.

## 📋 Table of Contents

1. [Activities](#activities)
2. [Fragments](#fragments)
3. [Lifecycle and State Management](#lifecycle-and-state-management)
4. [Navigation and Communication](#navigation-and-communication)
5. [Advanced Concepts](#advanced-concepts)

## Activities

### 🔹 What is an Activity in Android?
An Activity is a fundamental component of an Android app that represents a single screen with a user interface. It's responsible for creating the window in which UI components are placed.

### 🔹 What is the lifecycle of an Activity?
The Activity lifecycle consists of several callback methods:
- `onCreate()`
- `onStart()`
- `onResume()`
- `onPause()`
- `onStop()`
- `onDestroy()`

### 🔹 What is the purpose of onCreate() method?
The `onCreate()` method is called when the activity is first created. It's used to perform one-time initialization, such as creating views and binding data.

## Fragments

### 🔹 What is a Fragment?
A Fragment represents a portion of the user interface in an Activity. It's a modular section of an activity that has its own lifecycle and can be added or removed while the activity is running.

### 🔹 What is a FragmentManager?
FragmentManager is the class responsible for performing actions on your app's fragments, such as adding, removing, or replacing them, and adding them to the back stack.

### 🔹 What is the difference between Fragment and View?
A Fragment is a self-contained component with its own lifecycle that can be reused across multiple activities, while a View is a UI widget that renders something on the screen and handles user interactions.

## Lifecycle and State Management

### 🔹 What is the purpose of onSaveInstanceState()?
`onSaveInstanceState()` is called before an activity may be killed so that it can save its state. It's used to preserve the UI state across configuration changes or when the system kills and recreates the activity.

### 🔹 What is the purpose of setRetainInstance(true) in Fragments?
`setRetainInstance(true)` allows a fragment to be retained across Activity re-creation (such as when rotating the screen). This can be useful for retaining expensive objects or long-running operations.

## Navigation and Communication

### 🔹 What is the difference between startActivity() and startActivityForResult()?
`startActivity()` is used to start a new activity without expecting a result back, while `startActivityForResult()` is used when you expect a result from the started activity.

### 🔹 How do Fragments communicate with their host Activity?
Fragments typically communicate with their host Activity through interfaces. The Fragment defines an interface, and the host Activity implements it.

### 🔹 What is a BackStack in Android?
The BackStack is a stack of Fragment transactions that allows the user to reverse a fragment transaction (navigate backwards) by pressing the back button.

## Advanced Concepts

### 🔹 What is a DialogFragment?
DialogFragment is a subclass of Fragment that can be used to display a floating dialog. It's a more flexible and reusable alternative to using the Dialog class directly.

### 🔹 What is a SingleTaskActivity?
A SingleTaskActivity is an activity with a launchMode of "singleTask". It allows only one instance of the activity to exist at a time in the task stack.

### 🔹 What is a nested fragment?
A nested fragment is a fragment that is placed inside another fragment, rather than directly in an activity.

### 🔹 What is the difference between FragmentPagerAdapter and FragmentStatePagerAdapter?
FragmentPagerAdapter keeps every created Fragment in memory, while FragmentStatePagerAdapter destroys Fragments as the user navigates to other pages, minimizing memory usage.

---