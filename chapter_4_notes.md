## Chapter 4. Data Abstractions

Important quotes from the book

### Basics

#### One struct - One module

> Each module may define only one struct, which can then be used to create new instances and pattern-match on them.

> There is a tight relation between structs and modules. A struct may exist only in a module, and a single module can define only one struct.


#### Lack of data privacy/encapsulation

> This demonstrates that data privacy can’t be enforced in functional abstractions; you can see the naked structure of the data. 

> But as a client of a data abstraction, you shouldn’t rely on its internal representation, even though it’s visible to you. You shouldn’t pattern-match on the internal structure or try to extract or modify individual parts of it. The reason is that a proper abstraction, such as HashDict, doesn’t guarantee what the data will look like.

The problem here is less experienced developers, or those pressed for time, will try to take advantage of this “loophole”. That _could_ make your code more brittle if not careful.

#### Useful for old-school debugging: 

> This works because IO.inspect/1 prints the data structure and then returns that same data structure unchanged.


#### Updating deep structures 

> The original structure can be modified elegantly using the Kernel.put_in/2 macro

> It’s also worth noting that Elixir provides similar alternatives for data retrieval and updates in the form of the get_in/2, update_in/2, and get_and_update_in/2 macros. The fact that these are macros means the path you provide is evaluated at compile-time and can’t be built dynamically.

### Protocols

Protocols are like interfaces (in the Java parlance)

Define implementation of a protocol with `defimpl` macro:
```
    defimpl __, for: __ do
        ...
    end
```

## Notes from the Hangout...

Presenting: Geoff
Notes: Anthony

Found this chapter really interesting!

  - Data abstractions are very powerful
  - "This chapter got me thinking about writing idiomatic Elixir"

The way that you deal with data structures is through the module...

In elixir you always have the ability to probe the data structure, but you should use the interface provided by the module.

Chapter presents a todo list

When you have a deeply nested structure, you need to replace everything up the hierarchy with a copy, all the way up the chain

Benefit of immutability is that because you have to make a copy, if there is a copy, and there is an error, data isn't changed

Excited to work with Ecto[1][2]
Excited to work in a language that has protocols
  - footnote, but <description of protocol>
  - prevents a similar problem in Ruby when a method is left out

Protocol Consolidation, what is it?

new is not a reserved keyword used as a contructor
  - you can use anything

Geoff: What did people think?

Allison: "Didn't make it all the way through..." But excited to work through examples and get more "in the weeds".

Howard: Left wondering after reading the chapter, "Is this what it's like when you build out something 'enterprisey'" The language feels really comfortable. Reminded of past efforts with Scheme.

Tim: Talked about pattern matching and comparisons with coding in Ruby.

Corey: About protocols... I don't use the builtin protocols at all. "Keeping the rope shorter" As to structs, there's no ORM in Ecto.... [sorry, lost the thread]

Now chooses Phoenix over Rails because there's more of a safety net.

Howard: You can use RUM[3] in Rails. ... Geoff, what are the differences between Rails and Elixir that stand out?

Geoff: Contructors? A single way to accomplish things. Logical constructs. Since there are fewer options, in terms of ways to do something, you don't get paralized by choice. But, maybe it's just because I'm new to the language?

Allison: About testing... discussed at last Elixir meetup, is there something like RSpec? Testing as a thing in Elixir is far different than in Rails. Since things are simplier, there's not so great a need for something like RSpec.

ref:
1. Ecto https://hexdocs.pm/ecto/Ecto.html
2. https://github.com/elixir-ecto/ecto
3. RUM https://github.com/chneukirchen/rum
