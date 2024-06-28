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
