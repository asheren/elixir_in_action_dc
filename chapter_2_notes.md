Anthony presenting:

This chapter is mostly an overview of some of the basics of the language things. There are lots of references to things that will be covered more in depth in the future.

Chapter iteself is pretty light on detail.

## Building Blocks

Building blocks that goes over the basics of popular items like datatypes and operators or things to expect.
The info goes into a bit more detail with some good examples.

Starts with the point that in Elixir data is immutable but variables are mutable.

Once a memory location is occupied with data it can't be modified until it's released.

Elixir app has modules and functions that make up those modules.

Clojure does something similar (with immutable data); there's a good explanation of the concept [here](http://clojure.org/about/state).

`def` and `defmodule` are macros and not keywords. More info will be given on those later in the book.

The pipeline operator is a significant function. The argument on the left side of the operator is fed in as the right side.

Arity, for iterative functions can be helpful. There's 1 version of the function when you have a bunch of things in a list and then another version with a different arity number that is the function when you have done the thing to the list and have a final result. The concept for arity exists in other languages through concepts like currying, etc. The arity is part of the function name that you generally don't see unless you're passing it into another function.

Not possible to have a function that accepts a variable number of arguments.

Module attributes: type specifications with the `dializer` tool and `@spec` to get documentation are pretty cool and important. The `h` function here is also really great. It acts as a help and documentation accessor in runtime which is awesome. It's metadata for the function or module (also a concept in clojure).

Recommendation: http://www.exercism.io/languages/elixir/exercises

## Types highlights

- Division always returns a float

- Atoms are like symbols in ruby.

- Notion of aliases

- True and false are symbols as well as nil

- `nil` as a symbol is cool because you can do conditionals or pattern matching within the code which is interesting

- `is_atom nil` returns `true`

- Tuples: fixed size

- List: dynamic variable size. Look like arrays but operate like a singly linked list.

- Immutability: functions are free of side effects and there's data consistency.

- **note:** `HashDict`s are obsolete now and `map` should be used

- Map performance details [here](http://elixir-lang.org/getting-started/keywords-and-maps.html#maps) (Note at the bottom) Elixir 1.2 and above have performant maps

- Binaries play an important role in support for strings. Helpful when you work with parsing binary files or getting raw bytes. Like programming against the bytes of a file. Let's you cleanly define protocol definition of what you're expecting from the network.

- Strings: `sigils` are an interesting syntax.

- First class functions or lambdas or anonymous functions. Closures are interesting because you're capturing the data at the time it was captured.

We ended by jumping into the shell and just running a few of the functions and commands that were discussed in the chapter.

**Interesting example about functions**
```
&IO.puts35/31
&IO.puts35/31
```
puts35 doesn't exist, with or w/o arity 31





