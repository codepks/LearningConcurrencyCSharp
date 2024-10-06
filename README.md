# Task
## Task.Run(() => func())
It wraps around a call to make it syncronous if it is not syncronous.

# Async and await

[source](https://www.youtube.com/watch?v=2moh18sh5p4&t=46s&ab_channel=IAmTimCorey)

1. Make you function return type as  `Task` if it is having an async task
2. `await` keyword says : Run this asyncronously but wait for the results, like wait on something
    - Because the called for this function can continue its work while waiting for this task to finish
    - Once it gives back the results it will continue from there
    - Even though it is waiting it gives user interface the control to run its task
3. `await` blocks the method execution from going to next
4. To run parallel task you need to
    - The list of tasks run asyncronously amongst them
    - since there is no `await` that's why there is no blocking amongst them
    - Add your smaller tasks into  `Task` list or `Thread` pool in C++
    - Put `await` only in case of `Task.WhenAll(taksList)`
      
# await
[source : microsoft](https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httpclient.getbytearrayasync?view=net-8.0)
1. Until the `await` completes it suspends the function it is called in
2. When the current function is suspended,the control is returned to the called function
3. For e.g. the click event returns the control to the UI so that UI can continue its work


# Main Thread and Worker Thread

## Main Thread
Definition: The main thread is the primary thread of execution in a program. It is created by the operating system when the program starts running and is responsible for executing the main entry point of the application.

### Role:

1. In most applications (especially GUI applications), the main thread is responsible for initializing the application, creating the user interface, and handling user interactions.
2. It often runs in a single-threaded environment where all parts of the application must respond to events in a specific order.
3. Blocking: If the main thread is blocked (e.g., waiting for a long network operation to complete), the entire application can become unresponsive to user input.
4. This is why it's crucial to keep the main thread responsive, especially in GUI applications.

## Worker Thread
Definition: Worker threads are secondary threads created to perform background operations. They run independently of the main thread and can handle time-consuming tasks without blocking the main thread.

### Role:

1. Worker threads are useful for performing tasks such as data processing, file I/O, network requests, or any other operations that are expected to take a significant amount of time.
2. By offloading these tasks to worker threads, applications can remain responsive, allowing the main thread to continue processing user inputs and updating the UI.

## Creation:

1. Worker threads can be created in various ways, including using thread pools, tasks, or explicit thread management using languages and frameworks that support multi-threading.
2. Examples include using Thread, Task, or BackgroundWorker in .NET, as well as new Thread() in Java.
3. Example Scenario
4. Without Worker Threads: In a simple desktop application, if the main thread is responsible for fetching data from a remote server, it might cause the UI to freeze until the data is retrieved. Users would be unable to interact with the application during this wait time.
5. With Worker Threads: By creating a worker thread to handle the data retrieval, the main thread can continue to process user inputs and keep the UI responsive.
6. Once the data is fetched, the worker thread can notify the main thread to update the UI with the new data.

# Dispatcher

```
  Application.Current.Dispatcher.Invoke(() =>  
            {  
                ProgressBar.Value = i; // Update UI element  
            });
```
1. Dispatcher is a vital component used for managing the execution of code on the UI thread
2. A Dispatcher is an object that provides a mechanism for executing code on the thread that the Dispatcher is associated with.
3. Typically, this is the main UI thread of an application. It is designed to facilitate communication between different threads, particularly when you need to update the UI from a background thread.
4. This is crucial in UI applications where only the UI thread can safely modify UI elements.
5. The Dispatcher can queue methods to be executed on its thread.
6.  Dispatcher allows developers to specify a priority for the operations. This can dictate the order in which the actions will be executed.  
