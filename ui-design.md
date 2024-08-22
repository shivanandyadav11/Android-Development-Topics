# User Interface (UI) Design

1. Q: What are the main types of layouts in Android?
   A: The main types of layouts in Android are LinearLayout, RelativeLayout, FrameLayout, ConstraintLayout, and TableLayout.

2. Q: What is the ConstraintLayout?
   A: ConstraintLayout is a flexible layout that allows you to create large and complex layouts with a flat view hierarchy. It's the recommended layout for building responsive UIs.

3. Q: What is the difference between `wrap_content` and `match_parent`?
   A: `wrap_content` sizes the view to its content, while `match_parent` expands the view to fill its parent container.

4. Q: What is a ViewGroup?
   A: A ViewGroup is a special view that can contain other views (called children). It's the base class for layouts and views containers.

5. Q: What is the purpose of the `res/values` folder?
   A: The `res/values` folder contains XML files that define resources such as strings, colors, dimensions, and styles.

6. Q: What is a nine-patch image?
   A: A nine-patch image is a stretchable bitmap graphic that automatically resizes to accommodate the contents of the view and the size of the screen.

7. Q: What is the difference between `px`, `dp`, and `sp` units?
   A: `px` is pixels, `dp` is density-independent pixels (for consistent sizing across different screen densities), and `sp` is scale-independent pixels (for text sizes, adjusts based on user's font size preference).

8. Q: What is Material Design?
   A: Material Design is a design system created by Google that provides guidelines for visual, motion, and interaction design across platforms and devices.

9. Q: What is a RecyclerView?
   A: RecyclerView is a more advanced and flexible version of ListView that's used to efficiently display large sets of data in a scrollable list.

10. Q: What is the purpose of the `android:id` attribute?
    A: The `android:id` attribute is used to uniquely identify a view in the layout, allowing you to reference it in your Java or Kotlin code.

11. Q: What is a custom view?
    A: A custom view is a user-defined View subclass that can be used to create unique UI components not provided by the standard Android framework.

12. Q: What is the difference between `View.GONE` and `View.INVISIBLE`?
    A: `View.GONE` completely removes the view from the layout, while `View.INVISIBLE` makes the view invisible but still takes up space in the layout.

13. Q: What is a style in Android?
    A: A style is a collection of attributes that specify the appearance and format for a view. It can be applied to individual views or an entire activity.

14. Q: What is a theme in Android?
    A: A theme is a style applied to an entire Activity or application, rather than an individual view.

15. Q: What is the purpose of the `res/drawable` folder?
    A: The `res/drawable` folder contains graphical files (such as .png, .jpg, .gif) or XML files that describe drawable shapes or colors.

16. Q: What is a fragment?
    A: A fragment represents a portion of the user interface in an activity. It's like a modular section of an activity that has its own lifecycle.

17. Q: What is the purpose of `LayoutInflater`?
    A: `LayoutInflater` is used to instantiate layout XML files into their corresponding View objects at runtime.

18. Q: What is the difference between `ListView` and `RecyclerView`?
    A: `RecyclerView` is more flexible and efficient than `ListView`. It enforces the use of the ViewHolder pattern and allows for horizontal scrolling and more customization.

19. Q: What is the purpose of `android:layout_weight` in LinearLayout?
    A: `android:layout_weight` specifies how much of the extra space in the LinearLayout will be allocated to the view.

20. Q: What is a CoordinatorLayout?
    A: CoordinatorLayout is a super-powered FrameLayout, designed to be used as a top-level container for your UI. It allows for advanced scrolling behavior and animations.
