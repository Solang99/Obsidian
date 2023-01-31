Determines which thread or thread pool the corutine run on.
Different dispatcher are avaible depending on task specify.


### Common dispatchers 
- **Main**
	Used to update main in ui driven application
- **Default**
	Used for cpu intensive work ( ex -> image processing)
- IO
	Usefull for network communication or reading/writing files
- **Unconfined**
	Starts the corutines in the inherited dispacher that called it
- **newSinglethreadContext("MyThread")**
	Force a creation of new thread, ofc this should be used very carefull

Ex:
```kotlin
launch(Dispatchers.Default){...} // Very intensive cpu process
```


### WithContext
allows us to easly change a context of a corutine, it can be done thanks the dispatchers.
	```kotlin
launch(Dispatcher.Default){
	//default context
	withContext(Dispatcher.IO){
		// IO Context
	}
}
```
