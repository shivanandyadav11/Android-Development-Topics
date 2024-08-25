# 🚀 Kotlin Coroutines: Interview Questions & Answers

Welcome to the ultimate guide for mastering Kotlin Coroutines interview questions! This repository contains a curated list of medium and tough questions to help you prepare for your next big interview.

## 📚 Table of Contents

- [Medium Difficulty Questions](#medium-difficulty-questions)
- [Tough Questions](#tough-questions)

## 📚 More detailed content

1. [Coroutine Basics](./kotlin-coroutines/coroutine-basics-qa.md)
2. [Coroutine Scopes](./kotlin-coroutines/coroutine-scopes-qa.md)
3. [Suspending Functions](./kotlin-coroutines/suspending-functions-qa.md)
4. [Coroutine Context and Dispatchers](./kotlin-coroutines/coroutine-context-and-dispatchers-qa.md)
5. [Job and Deferred](./kotlin-coroutines/job-and-deferred-qa.md)
6. [Coroutine Builders](./kotlin-coroutines/coroutine-builders-qa.md)
7. [Exception Handling in Coroutines](./kotlin-coroutines/exception-handling-in-coroutines-qa.md)
8. [Cancellation and Timeouts](./kotlin-coroutines/cancellation-and-timeouts-qa.md)
9. [Channels](./kotlin-coroutines/channels-qa.md)
10. [Flow API](./kotlin-coroutines/flow-api-qa.md)
11. [Testing Coroutines](./kotlin-coroutines/testing-coroutines-qa.md)
12. [Coroutine Design Patterns](./kotlin-coroutines/coroutine-design-patterns-qa.md)
13. [Structured Concurrency](./kotlin-coroutines/structured-concurrency-qa.md)
14. [Asynchronous Programming with Coroutines](./kotlin-coroutines/asynchronous-programming-with-coroutines-qa.md)
15. [Coroutines in Android Development](./kotlin-coroutines/coroutines-in-android-development-qa.md)

## Medium Difficulty Questions

### 1. 🏗️ `launch` vs `async`

**Q: What is the difference between `launch` and `async` coroutine builders?**

<details>
<summary>View Answer</summary>

Both `launch` and `async` are coroutine builders, but they have different use cases:
- `launch`:
  - Starts a coroutine that doesn't return a result
  - Returns a `Job` object
- `async`:
  - Used when you need to return a result from the coroutine
  - Returns a `Deferred` object (a light-weight non-blocking future)

</details>

### 2. 🏢 Structured Concurrency

**Q: Explain the concept of structured concurrency in Kotlin Coroutines.**

<details>
<summary>View Answer</summary>

Structured concurrency is a design principle ensuring that coroutines are not lost or leaked:
- Coroutines follow a parent-child hierarchy
- When a parent coroutine is cancelled, all its child coroutines are cancelled too
- A parent coroutine waits for all its children to complete before completing itself

This helps in managing the lifetime of coroutines and prevents resource leaks.

</details>

### 3. ⏸️ Suspend Functions

**Q: What is a suspend function and how does it differ from a regular function?**

<details>
<summary>View Answer</summary>

A suspend function is a function that can be paused and resumed. Key differences:
- Marked with the `suspend` keyword
- Can only be called from within a coroutine or another suspend function
- Can use other suspend functions like `delay()` without blocking the thread
- Transformed into a state machine by the Kotlin compiler

</details>

### 4. 🛡️ Exception Handling

**Q: How do you handle exceptions in coroutines?**

<details>
<summary>View Answer</summary>

Exceptions in coroutines can be handled using:
- Try-catch blocks within the coroutine
- `CoroutineExceptionHandler` for uncaught exceptions
- `SupervisorJob` to prevent sibling coroutines from cancelling each other
- `runCatching` for functional-style exception handling

</details>

### 5. 🧩 Coroutine Context

**Q: What is a coroutine context and what are its main elements?**

<details>
<summary>View Answer</summary>

A coroutine context is a set of elements that define the behavior of a coroutine. Main elements include:
- Job: Controls the lifecycle of the coroutine
- Dispatcher: Determines which thread(s) the coroutine runs on
- CoroutineName: Assigns a name to the coroutine for debugging purposes
- CoroutineExceptionHandler: Handles uncaught exceptions

</details>

## Tough Questions

### 1. 🔬 `coroutineScope` vs `supervisorScope`

**Q: Explain the difference between `coroutineScope` and `supervisorScope`. When would you use each?**

<details>
<summary>View Answer</summary>

Both create a new coroutine scope, but differ in exception handling:

`coroutineScope`:
- Cancels all children if any child fails
- Propagates the exception to its parent
- Use for all-or-nothing execution of child coroutines

`supervisorScope`:
- Doesn't cancel other children when one fails
- Doesn't propagate exceptions to its parent automatically
- Use for independent execution of child coroutines

Use `coroutineScope` for dependent tasks, `supervisorScope` for independent tasks.

</details>

### 2. 🚫 Coroutine Cancellation

**Q: How does coroutine cancellation work, and what are cancellation points?**

<details>
<summary>View Answer</summary>

Coroutine cancellation works cooperatively:
1. Job's state changes to cancelling
2. `CancellationException` is thrown at the next cancellation point
3. Coroutine runs its cancellation logic and terminates

Cancellation points are typically suspend functions like `yield()`, `delay()`, or `withContext()`.

To make computations cancellable, periodically check `isActive` flag or call `yield()`.

</details>

### 3. ⏳ `withContext()` vs `withTimeout()`

**Q: What is the difference between `withContext()` and `withTimeout()`, and when would you use each?**

<details>
<summary>View Answer</summary>

- `withContext(context) { ... }`: Switches the context of a coroutine
  - Use to change dispatchers (e.g., moving to a background thread)

- `withTimeout(timeMillis) { ... }`: Sets a timeout for a block of suspending code
  - Throws `TimeoutCancellationException` if exceeded
  - Use to limit execution time of an operation

</details>

### 4. 🌊 Flow

**Q: Explain the concept of flow in Kotlin Coroutines and how it differs from sequences.**

<details>
<summary>View Answer</summary>

Flow is for handling streams of asynchronous data. Differences from sequences:
- Asynchronous (sequences are synchronous)
- Can emit values computed asynchronously
- Supports back-pressure out of the box
- Has built-in cancellation support
- Can use coroutine contexts and dispatchers

Used for handling streams from async operations like network requests or database queries.

</details>

### 5. 🔀 `select` Expression

**Q: How does the `select` expression work in Kotlin Coroutines, and what are its use cases?**

<details>
<summary>View Answer</summary>

`select` allows awaiting multiple suspending functions simultaneously, selecting the first available. Use cases:
- Receiving from multiple channels
- Combining timeouts with other operations
- Racing multiple asynchronous operations

Example:
```kotlin
select<Unit> {
    channel1.onReceive { value ->
        println("Received from channel1: $value")
    }
    channel2.onReceive { value ->
        println("Received from channel2: $value")
    }
}
```

</details>

### 6. 📡 Channel vs Flow

**Q: What are the differences between `Channel` and `Flow`, and when would you use each?**

<details>
<summary>View Answer</summary>

Channels:
- Hot streams (active even without collectors)
- Multiple senders and receivers
- For coroutine-to-coroutine communication
- Built-in back-pressure support

Flows:
- Cold streams (only active when collected)
- Single sender, multiple collectors
- For asynchronous data streaming
- Rich set of operators for data manipulation

Use Channels for coroutine communication or shared event streams. Use Flow for async sequences, especially with functional-style operations.

</details>

## 🎉 Conclusion

Mastering these concepts will significantly boost your understanding of Kotlin Coroutines and prepare you for challenging interview questions. Good luck with your interview preparation!

---

📌 Don't forget to star this repo if you find it helpful! For more in-depth information, check out the [official Kotlin Coroutines documentation](https://kotlinlang.org/docs/coroutines-overview.html).

