## Chapter 5. Concurrency Primitives

Primitives

* `spawn`
* `receive`
* `send`

`receive` will _block_ until it receives a message matching the input pattern

From section 5.3.1:

> This can be used to implement a server process. You need to run the endless loop and wait for a message in each step of the loop. When the message is received, you handle it and then continue the loop. Let’s try this and turn the query example into a server process. The basic sketch is provided in the following listing.

> This loop usually isn’t CPU intensive. Waiting for a message puts the process in a suspended state and doesn’t waste CPU cycles.

