# Web-Server Simulation

<br>

This project uses Java and then tries to simulate differnt approaches on how we can effectively handle data at the server side and implements 3 main approaches to handle this problem.

<br>

## Single Threaded

For the single threaded approach the Server tries to listen to the port for any incoming clients and when there is a client request it creates a _socket_ connection between the server and the client.

```
    serverSocket.setSoTimeout(10000);
```

The timeout function is used to simulate work being done by the server and the connection being open between the client ans server during this time.

<br>

## MultiThreaded

For the multithreaded implementation, we first define the `Thread` for each of the client and server connections being made which allows the system to carry out multiple requests at once until the request is blocked due to I/O in which case context switching takes place. This is useful as the server can now utilize all of its memory concurrently but the problem here is that it can only make new threads to a certain limit.
These problems are further solved in threadpooling.

<br>

## Thread Pool

In this approach, we start be defining a `poolSize` which will be the maximum threads created by the server at that time and instead of creating and deleting the existing the threads for each process, we simply have to follow an event loop and the processes are given specific thread.

When all the threads are busy, the client is sent to a queue after which it will be allocated a thread from the pool only after another process is finished or we have to `context switch` because of I/O conidtions.
