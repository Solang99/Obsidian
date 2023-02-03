Grpc (Remote procedure code), ands allow to directally call a function on the server

### Why To use [[Protobuffer]]
- Compared to json has a bug difference in payload size
![[Pasted image 20230202165526.png]]

- Less CPU intensive (efficent serialization deserialization)
- Faster
-
### HTTP2
HTTP1 sucks because: 
 - HTTP1 basically open a connection for request (open a connection -> make request -> close connection) 
 - HTTP1 not compress headers so it can be pretty big and it will cause more latency
 - Only support request/response pattern
 
 HTTP2 is more efficent because:
 - Open a single TCP request
 - Multiplexing: Server and client can push in parallel multiple request on same connecton
 - Data are compressed in binary 
 - By default it's need ssl so it's more secure than http1

## API in Grpc
there are 4 type of api that we can use in GRPC
	- Unary: Similar to rest api, the client sent one request and server will repaly with one response
	- Server Straming: The client sent one request and the seerver can return more response when ready, usefull to update client in real time
	- Client Streaming: The clinet send multiple request and server return one response, usefull for some kind of update
	- Bi directional straming: 
 ![[Pasted image 20230202170630.png]]
```C
service GreetService{
	// Unary
	rpc Greet(GreetRequest) returns(GreetResponse) {};
	// Server straming
	rpc GreetManyTimes(GreetRequest) returns (stram GreetResponse) {};
	// Client streaming
	rpc LongGreet(stream GreetRequest) returns (GreetResponse) {};
	// Bi directional straming
	rpc GreetEveryOne(stram GreetRequest) returns (stram GreetResponse) {};
}
```


Server can be request many request in parallel (_async_)
Client side we can chose to use an async or blocking approch
![[Pasted image 20230202171850.png]]


#api