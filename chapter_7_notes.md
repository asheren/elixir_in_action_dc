# Chapter 7 - Building a concurrent system



## 7.1: Mix

Your main entry point to running anything. It seems a combination of a few things from other systems: rake, bundler, maven, scaffolding

## 7.2

In the discussion of this section, we started asking many questions without having answers for all of them.

Here we seem to be hurting for a lack of error handling.

This pattern of using one global server where you instantiate it and have to pass it around every time you use the module: is there a way to implicitly set that up as needed?
Could we use mix to start them? Is this a matter of keeping abstraction layers separate, waiting for talk about supervisors that we haven’t gotten to yet in this chapter?

## Notes not section-specific
Phrasing like “this is a bit of a hack” is used five or six times in this chapter. Are these due to weaknesses inherent in Elixir or Erlang? Are these problems that [Ecto](https://github.com/elixir-ecto/ecto) or other tools get brought in to solve? Or is the book being structured so that we aren’t overwhelmed with every bit of knowledge at once, and the answer to some of these pains are coming up next? Is this beginning of concurrency and deliberately limited?

There is some problem here in the way that processes depend on each other. As an example, we’re doing writes with a cast so there’s no guarantee that data is written. These unguaranteed writes are then followed by reads, and problems could get introduced there.

We talked about mutexes. A mutex is like a group conversation where you've made a rule that the only person allowed to talk is whoever is holding a certain stick (or other predefined item). You then pass this talking stick around when you're done talking to give others a chance.

The process-based pattern described in this chapter frees us from having to directly manage mutexes, which has some benefits.
Each process is responsible for one specific set of resources. Each process will then work through its queue one item at a time, preventing competition for the resources that process manages.

We discussed ways process differently could handle their queues of incoming messages differently. What do you do when you don’t have capacity or are backlogged? There could be queues that dump old messages after a certain max limit is reached, or queues that dump new messages. If you’re dropping messages on the floor, is that the definition of an unreliable system? How do you handle backpressure, the concept of slowing down the systems feeding messages in to the backlogged system? Some of this is inherent in using `call` (as opposed to using `cast`), as `call` makes the system sending the message wait for a response. You could also add your own means of backpressure.

We talked a bit about a fan-out structure of the processes in this chapter.

It was also mentioned, when looking at removing bottlenecks, how each client can ask “give me a worker” instead of routing every single message through the main database process.


## On exercises and examples

There was a lot in this one if you tried to do the exercises. There is some pain in how the book doesn’t help with testing. No intro to testing in Elixir is yet provided.

A note that you may want to change [the example files](https://github.com/sasa1977/elixir-in-action) to not lock you to their version of Elixir. In the mix file:

```elixir
def project do
  [ app: :todo,
    version: "0.0.1",
    elixir: "~> 1.0",
    deps: deps
  ]
end
```
Where the operative change is the `elixir: "~> 1.0"` line.


As a compliment to the exercises in this chapter, you may want to check out [Exercism](http://exercism.io) or the [Pragprog](https://pragprog.com/book/elixir/programming-elixir) book, since they’re more focused on the language. “Elixir in Action”, and especially this part of it, is focused more on the platform. 
