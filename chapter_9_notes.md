# Chapter 9 - Isolating error effects

## Summary

3 concepts:
* Supervisor trees
* Starting workers dynamically
* Philosophy ("let it crash")

Thoughts:

* It can be difficult to keep track of dependencies between things; possibility
  of cyclic dependencies (without realizing it).
* Hard to understand design decisions of the example(s).

## 9.1: Supervision Trees

What supervisor types/error handling patterns are most common? Is there one
that's used 90% of the time, then others are for edge/specific cases?

Idea: take examples of use from the book, turn into test cases

* [ExUnit](https://hexdocs.pm/ex_unit/ExUnit.html)
* [Doctests](https://hexdocs.pm/elixir/writing-documentation.html#doctests)

Example test code:

```elixir <test/todo/database_worker_test.exs>
defmodule Todo.DatabaseWorkerTest do
  use ExUnit.Case
  doctest Todo.DatabaseWorker

  test "it can start" do
    Todo.ProcessRegistry.start_link
    Todo.DatabaseWorker.start_link( "./persist/", 5)
  end
end
```

```elixir <test/test_helper.exs>
ExUnit.start()
```

Elixir quickstart: `docker run -t -i --rm elixir iex` (if you don't have elixir
installed locally)

*via tuples* - send a message through an intermediary rather than directly to a
process (let something else provide the target process).

```elixir
GenServer.start_link(
  Todo.DatabaseWorker,
  db_folder,
  name: {:via, Todo.ProcessRegistry, {:database_worker, 1}}
)

GenServer.call(
  {:via, Todo.ProcessRegistry, {:database_worker}, 1},
  {:get, key}
)

GenServer.cast(
  {:via, Todo.ProcessRegistry, {:database_worker}, 1},
  {:store, key, data}
)
```

## 9.2: Starting workers dynamically

Supervisor strategies (from [hexdocs](https://hexdocs.pm/elixir/Supervisor.html#module-strategies)):

* `:one_for_one`  
  If a child process terminates, only that process is restarted.
* `:one_for_all`  
  If a child process terminates, all other child processes are terminated and
  then all child processes (including the terminated one) are restarted.
* `:rest_for_one`  
  If a child process terminates, the “rest” of the child processes, i.e., the
  child processes after the terminated one in start order, are terminated. Then the terminated child process and the rest of the child processes are restarted.
* `:simple_one_for_one`  
  Similar to :one_for_one but suits better when dynamically attaching children.
  This strategy requires the supervisor specification to contain only one child. Many functions in this module behave slightly differently when this strategy is used.

Potential use for :rest_for_one - "Pipeline" processes (or layers), where each
process depends on the one(s) after it/below it.

## 9.3: "Let it crash"

Restart things for error recovery, rather than trying to handle everything that
might go wrong.

**error kernel** - The part of the program that CANNOT go down. Keep this
surface area as small as possible.

Expected vs unexpected errors: handle expected errors, crash and restart on an
unexpected error.

## Other Notes

"Any sufficiently complicated concurrent program in another language contains
an ad hoc informally-specified bug-ridden slow implementation of half of
Erlang."  
_[Virding's First Rule of Programming](http://rvirding.blogspot.com/2008/01/virdings-first-rule-of-programming.html)_

Hexdocs: [Supervisor](https://hexdocs.pm/elixir/Supervisor.html)
