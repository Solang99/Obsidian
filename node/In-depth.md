- When we write code we are in the js level, when we lunch "node app" we move to the second. Nodejs to execute our code need to some dependency, the most importan one are the **V8** and ***libuv***.
- The **V8** is a engine that  allow us to execute js code outside a browser
- **Libuv** is a C++ library that allow js to access to os 

![[2023-01-29_18-42.png]]

## Event Loop
JavaScript has a runtime model based on an **event loop**, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks. This model is quite different from models in other languages like C and Java.

### Implementation of event loop (Sample)
```Javascript
// node myfile.js
const pendingTimers = [];
const pendingOSTasks = [];
const pendingOperations = [];

// Node does not launch event loop immediately exits the program, instead read first the entire file and then execute it
// Also the timers and tasks are recorded now
myfile.runContents();

//Decides if the loop should continue or not
function shouldContinue(){
    // Node js made three checks in this function:
        // 1. Check if there is any setTimeout,setInterval or setImmediate that needs to be executed
        
        // 2. Check if there is any pending OS tasks (like server listening to port)

        // 3. Check if there is any pending long running operations (like fs module)
    return pendingTimers.length || pendingOSTasks.length || pendingOperations.length;
}

// Now the event is launched
// Entire body execute in one 'tick'
while(shouldContinue()){
    // 1) Looks at pendingTimers and sees if any functions are ready to be called. setTimeout, setInterval

    // 2) Looks at pendingOSTasks and pendingOperations and calls relevant callbacks  

    // 3) Pause execution. Continue when...
        // - a new pendingOSTask is done
        // - a new pendingOperation is done
        // - a timer is about to complete

    // 4) Look at pendingTimers. Call any setImmediate
    
    // 5) Handle any 'close' events (ex: called when a stream is closed)
}
// exit back to terminal
```

### Is node single thread?
The event loop is based on a single thread so it will not take advantage of multiple cose **BUT** some node framework can be not a single thread![[Pasted image 20230201114238.png]]

- What function in node std use the [[Thread pool]]? 
	- All 'fs' functions, crypto stuff and other!
- how does threadPool stuff fit into the event loop?
	- Task running in the threadpool are the 'pendingOperation' mentioned above.
	
- What function in node std library use OS's async ? 
	- Almost everthing around networking for all OS's
- How does async stuff fit into the event loop?
	- Task running in the threadpool are the 'pendingOsTasks' mentioned above.

#thread 