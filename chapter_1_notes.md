## Chapter 1. First Steps

### Main Goals/Strengths/Benefits of Erlang/Elixir

* High Availability & Concurrency
* Handling failures and being resilient
* Ability to scale, and inherently distributed 
* Responsiveness under load

BEAM: Bogdan/Bjorn’s Erlang Abstract Machine 
- analogous to JVM/CLR

Erlang has its own dedicated schedulers, manages lightweight processes above the OS level threads
- can see it in action with `:observer.start`

Elixir itself:
* simplifies erlang code
* more modern/accessible syntax
* pipeline operator for chaining functions cleanly

Does it have much greater interop than say, clojure/scala with java on jvm?
Seems like much of the boilerplate comes from OTP concepts?
