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
