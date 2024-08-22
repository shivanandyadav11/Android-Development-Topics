# Networking

1. Q: What permission is required to perform network operations in Android?
   A: The INTERNET permission is required. It's declared in the AndroidManifest.xml file:
   ```xml
   <uses-permission android:name="android.permission.INTERNET" />
   ```

2. Q: What is HttpURLConnection?
   A: HttpURLConnection is a class that represents a connection to an HTTP server and provides methods for sending requests and retrieving responses.

3. Q: What are some popular networking libraries for Android?
   A: Some popular networking libraries include Retrofit, Volley, and OkHttp.

4. Q: What is Retrofit?
   A: Retrofit is a type-safe HTTP client for Android and Java. It makes it easy to consume RESTful web services by turning your HTTP API into a Java interface.

5. Q: How do you typically use Retrofit to make a network request?
   A: You define an interface with annotated methods representing API endpoints, create a Retrofit instance, and then use the interface to make API calls.

6. Q: What is JSON?
   A: JSON (JavaScript Object Notation) is a lightweight data-interchange format that's easy for humans to read and write and easy for machines to parse and generate.

7. Q: How can you parse JSON in Android?
   A: You can use libraries like Gson or Moshi to parse JSON, or use the built-in JSONObject and JSONArray classes.

8. Q: What is the purpose of the Gson library?
   A: Gson is a Java library that can be used to convert Java Objects into their JSON representation and vice versa.

9. Q: What is a REST API?
   A: REST (Representational State Transfer) is an architectural style for designing networked applications. A REST API is a set of rules for building web services that follow REST principles.

10. Q: What is the difference between GET and POST HTTP methods?
    A: GET requests data from a specified resource, while POST submits data to be processed to a specified resource.

11. Q: What is SSL/TLS?
    A: SSL (Secure Sockets Layer) and its successor TLS (Transport Layer Security) are cryptographic protocols designed to provide communications security over a computer network.

12. Q: How can you make HTTPS connections in Android?
    A: You can use HttpsURLConnection or networking libraries like Retrofit or OkHttp, which handle HTTPS connections by default.

13. Q: What is a WebSocket?
    A: WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection.

14. Q: How can you handle network operations on the main thread?
    A: You shouldn't perform network operations on the main thread as it can lead to ANR (Application Not Responding) errors. Instead, use background threads, AsyncTask, or coroutines.

15. Q: What is the purpose of the Volley library?
    A: Volley is an HTTP library that makes networking for Android apps easier and faster. It provides automatic scheduling of network requests and support for request prioritization.

16. Q: What is OkHttp?
    A: OkHttp is an efficient HTTP client that supports modern protocols like HTTP/2 and SPDY. It can be used standalone or as a networking layer for other libraries like Retrofit.

17. Q: How can you check for network connectivity in Android?
    A: You can use the ConnectivityManager system service to check for network connectivity:
    ```kotlin
    val connectivityManager = context.getSystemService(Context.CONNECTIVITY_SERVICE) as ConnectivityManager
    val networkInfo = connectivityManager.activeNetworkInfo
    val isConnected = networkInfo != null && networkInfo.isConnected
    ```

18. Q: What is caching in the context of network requests?
    A: Caching is storing the results of network requests locally so that they can be quickly retrieved later, reducing the need for repeated network calls and improving app performance.

19. Q: How can you implement caching with OkHttp?
    A: OkHttp provides a Cache class that you can configure when building your OkHttpClient:
    ```kotlin
    val cacheSize = 10 * 1024 * 1024 // 10 MB
    val cache = Cache(context.cacheDir, cacheSize.toLong())
    val client = OkHttpClient.Builder()
        .cache(cache)
        .build()
    ```

20. Q: What is the purpose of the @Headers annotation in Retrofit?
    A: The @Headers annotation in Retrofit is used to add static headers to a request. For example:
    ```kotlin
    @Headers("Cache-Control: max-age=640000")
    @GET("/widget/list")
    fun widgetList(): Call<List<Widget>>
    ```
