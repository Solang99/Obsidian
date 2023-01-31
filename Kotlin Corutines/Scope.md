Provide lifecycle method for corutine, the mains kind of scopes are:

- **GlobalScope**: The scope of the corutine is the entire application, so the corutine will not stop until the application is running
```kotlin
GlobalScope.launch{
	delay(1000L)
	println("Global scope")
}
```

- **runBloking** : Create a scope and ruines a corutines in a blocking way
```kotlin
runBlocking{
	launch{
		delay(1000L)
		println("Bloking task")
	}
}
```
- **corutineScope**: Create a new scope and does not complete until all childer are compelte
```kotlin
corutineScope{
	delay(1000L)
	println("Custom corutine scope")
}
```
