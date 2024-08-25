# 🚀 Kotlin Coroutines: Mastering the Basics

Welcome to your comprehensive guide to Kotlin Coroutines! This README is designed to take you from a beginner to an advanced user through a series of carefully crafted questions and answers. Let's dive in!

## 📚 Table of Contents

- [Easy Questions](#-easy-questions)
- [Medium Questions](#-medium-questions)
- [Hard Questions](#-hard-questions)

## 🌱 Easy Questions

1. **What is a coroutine in Kotlin?**
   > A coroutine is a concurrency design pattern that simplifies asynchronous code execution in Kotlin.

2. **What's the main advantage of using coroutines?**
   > Coroutines help manage long-running tasks that might otherwise block the main thread, preventing app unresponsiveness.

3. **How do you start a new coroutine?**
   > Use coroutine builders like `launch` or `async`.

4. **What's the difference between `launch` and `async`?**
   > - `launch`: Starts a coroutine that doesn't return a result
   > - `async`: Starts a coroutine that returns a result

5. **What is a suspending function?**
   > A function that can be paused and resumed later, marked with the `suspend` keyword.

<details>
<summary>👉 Click for more easy questions</summary>

6. **How do you declare a suspending function?**
   > Add the `suspend` keyword before the function declaration.

7. **What's the purpose of the `delay` function?**
   > `delay` pauses the coroutine for a specified time without blocking the thread.

8. **Can you use regular functions inside a coroutine?**
   > Yes, both regular and suspending functions can be used inside a coroutine.

9. **What is a coroutine scope?**
   > A context that manages the lifecycle of coroutines.

10. **What happens when a coroutine is launched without a scope?**
    > It can lead to memory leaks as the coroutine may outlive the component that started it.

</details>

## 🏋️ Medium Questions

11. **How does structured concurrency work in Kotlin coroutines?**
    > It ensures that when a coroutine is cancelled, all its child coroutines are cancelled too, preventing leaks and making concurrent code more predictable.

12. **What is a coroutine context?**
    > A set of elements defining a coroutine's behavior, such as its dispatcher, job, and name.

13. **How can you switch between different threads in coroutines?**
    > Use different dispatchers like `Dispatchers.Main`, `Dispatchers.IO`, or `Dispatchers.Default`.

14. **What's the difference between `runBlocking` and `coroutineScope`?**
    > - `runBlocking`: Blocks the current thread
    > - `coroutineScope`: Suspends the current coroutine without blocking the thread

15. **How do you handle exceptions in coroutines?**
    > Use try-catch blocks or a `CoroutineExceptionHandler`.

<details>
<summary>👉 Click for more medium questions</summary>

16. **What is a coroutine job?**
    > A cancellable thing with a lifecycle, associated with every coroutine.

17. **How can you cancel a coroutine?**
    > Call the `cancel()` function on its job or scope.

18. **What's the purpose of the `yield()` function?**
    > It gives other coroutines a chance to run, improving fairness in scheduling.

19. **How do you create a custom coroutine context?**
    > Combine existing context elements or implement the `CoroutineContext.Element` interface.

20. **What's the difference between `async` and `withContext`?**
    > - `async`: Starts a new coroutine and returns a `Deferred` result
    > - `withContext`: Changes the context of the current coroutine and returns the result directly

</details>

## 🎓 Hard Questions

21. **How does coroutine continuation work under the hood?**
    > Coroutine continuation transforms suspending functions into state machines, with each suspension point becoming a state managed by the coroutine framework.

22. **What's the relationship between coroutines and Kotlin's sequence builders?**
    > Both use similar concepts of suspension and resumption. Sequence builders can be seen as synchronous coroutines that yield values one at a time.

23. **How can you implement a cooperative cancellation system using coroutines?**
    > Regularly check the `isActive` flag of the current coroutine and respond to cancellation by throwing a `CancellationException`.

24. **What are the potential pitfalls of using `GlobalScope` and how can they be mitigated?**
    > `GlobalScope` can lead to memory leaks and complicate testing. Mitigate by using structured concurrency and passing explicit scopes to functions that launch coroutines.

25. **How can you implement a custom coroutine dispatcher?**
    > Extend the `CoroutineDispatcher` class and override its `dispatch` method to define coroutine execution behavior.

<details>
<summary>👉 Click for more hard questions</summary>

26. **What's the difference between `supervisorScope` and regular coroutine scope?**
    > `supervisorScope` creates a scope where child failures don't affect each other or the parent. In a regular scope, any child failure cancels the entire scope.

27. **How can you implement a timeout mechanism without using `withTimeout`?**
    > Launch a separate coroutine that delays for the timeout period and then cancels the main coroutine if it's still active.

28. **How does flow backpressure work and how can you implement custom strategies?**
    > Flow backpressure manages situations where emissions are faster than collection. Implement custom strategies using operators like `buffer`, `conflate`, or by creating custom `FlowCollector` implementations.

29. **What are the implications of using coroutines with respect to thread safety in Kotlin/JVM?**
    > Coroutines don't guarantee thread safety by themselves. When working with shared mutable state, you still need appropriate synchronization mechanisms or state confinement to a single thread.

30. **How can you implement a custom coroutine builder with guaranteed behavior?**
    > Create a function that wraps an existing builder (`launch`, `async`, etc.) and applies the desired context or behavior before starting the coroutine.

</details>

---

🎉 Congratulations on making it through these questions! You're well on your way to mastering Kotlin Coroutines. Keep practicing and exploring, and you'll be a coroutine expert in no time!

📌 **Note**: This README covers the basics of Kotlin Coroutines. For more advanced topics and practical examples, check out the official [Kotlin Coroutines Guide](https://kotlinlang.org/docs/coroutines-guide.html).

---

💡 Did you find this guide helpful? Star the repository and share it with your fellow Kotlin developers!

