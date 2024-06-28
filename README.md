# Async and await

[source](https://www.youtube.com/watch?v=2moh18sh5p4&t=46s&ab_channel=IAmTimCorey)

1. Make you function return type as  `Task` if it is having an async task
2. `await` keyword says : Run this asyncronously but wait for the results
    - Because the called for this function can continue its work while waiting for this task to finish
    - Once it gives back the results it will continue from there
3. `await` blocks the method execution from going to next
4. To run parallel task you need to
    - Add your smaller tasks into  `Task` list or `Thread` pool in C++
    - Put `await` only in case of `Task.WhenAll(taksList)` 
