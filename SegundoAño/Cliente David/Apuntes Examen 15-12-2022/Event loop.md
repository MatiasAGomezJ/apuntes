![[recursive_error.png]]![[callstack_error.png]]###### Columna I

# How does JavaScript even work?
V8. Single threaded.

Actual definition: a single-threaded non-blocking asynchronous concurrent language. I have a callstack, an event loop, a callback queue som other API's and stuff.

V8 has a callstack and a heap.

![](https://i.imgur.com/HBL5hmm.png)

![](https://i.imgur.com/hvWkD8a.png)

The call stack
one thread == one call stack == one thing at a time

![](https://i.imgur.com/Erf5OJF.png)
![[callstack_error.png]]
![[recursive_error.png]]

## Blocking
What happens when things are slow?
In a single-threaded language we have to wait for each statement to finish
This is a problem because of browsers. The browsers, when a statement is executing, is stuck until said statement finishes.

## Solution: Asynchronous callbacks
![[asynchronous.png]]


JavaScript is single-threaded, but the browser sort of gives threads to work with, like ajax, serTimeout, between others.

The event loop sees the stack and if it's empty, pushes the callbacks inside the task queue.

[Video](https://www.youtube.com/watch?v=8aGhZQkoFbQ) 12:32
