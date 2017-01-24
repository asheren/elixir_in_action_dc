## Chapter 5. Concurrency Primitives

* new section of book, delves into the erlangy side of elixir


## Chapter 5: Concurrency primitives

### Principals

Concurrency is not parallelism.
Primitives

* `spawn`
* `receive`
* `send`

`receive` will _block_ until it receives a message matching the input pattern

From section 5.3.1:

> This can be used to implement a server process. You need to run the endless loop and wait for a message in each step of the loop. When the message is received, you handle it and then continue the loop. Let’s try this and turn the query example into a server process. The basic sketch is provided in the following listing.

> This loop usually isn’t CPU intensive. Waiting for a message puts the process in a suspended state and doesn’t waste CPU cycles.

### Working with processes

Talking about message passing, how we get cooperation between processes

### Stateful processes

Using tail recursion to achieve long-running processes

### Runtime considerations

Goes into processes as bottlenecks

Hone in on the notion that processes are a fundamental building block, but there
are still system considerations needed.  Messages are handled synchronusly

Unlimited process mailboxes, but beware of memory exhaustion

Shared nothing concurrency

> if the last thing a function does is call another function, then a simple
> jump takes place, rather than a stack push


Howard:  beyond just a loop, can also do a state machine, where each state is
represented by a specific handler method.

"If it seems like an OS, that's because we were absolutely thinking of it like one"

> Parralelization is not a remedy for poorly structured algorithms.
