# Kotlin Coroutines

* Coroutines are conceptually similar to a thread but are not bound to one particular thread, so they can suspend and execute in different areas.
* **Structured concurrency** - new coroutines can only be launched in a specific coroutine scope eg. RunBlocking. This means that they cannot be lost and do not leak errors.
* An outer scope cannot complete until all its children coroutines complete.
* Coroutines are much more lightweight than JVM threads and use less resource and memory, meaning less risk of out-of-memory errors.
