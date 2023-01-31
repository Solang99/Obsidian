If a corutine must return something we need to run it with ***async*** (instead of launch), the corutine then will return in form of a deferred (a sort of promise)


We we need the deferred value we  need to call the ***await*** (blocking call)

```kotlin
suspend fun getRandom() = Random.nextInt(1000)

...

val valueDeferred = GlobalScope.async{getRandom()}
// Some op here
val finalVal = valueDeferred.await() 
```