# Chapter 6 - Generic server processes

Chapters 5 & 6 seem like the "meat" of Elixir
For a different summary of this chapter, see the GenServer docs: https://hexdocs.pm/elixir/GenServer.html

## 6.1 - Implementing GenServer

Mostly a continuation of Chapter 5

## 6.2 - Using GenServer

### 6.2.1 OTP behaviours (with British spelling)

Ensure a module implements some required functions.  See the `@behaviour` docs at https://hexdocs.pm/elixir/Module.html

### 6.2.2
  `use` a module
  There's some metaprogramming magic happening to dump the module's functions into your module

### 6.2.3 The interface to GenServer
  - init, handle_cast, handle_call, handle_info
  - `cast` and `call` differences - `call` blocks for a response, while `cast` is fire-and-forget

### 6.2.4 Handling plain messages
  `handle_info` is kind of boilerplate - if you handle custom messages, you have to include a do-nothing catch-all.
  Why use this?  It's a catch-all for messages that aren't `call` or `cast`, ie VM housekeeping messages

### 6.2.6 Process life cycle
  See diagram on p 179
  Core of this is the "gen_server loop" in the center
    - translating between messages (to/from the client process) and function calls to `handle_cast` etc
    - right column are callbacks that you implement in your `GenServer` module

  Contrast between OO & Actor module  
    - cast/call is similar to the command/query separation that's considered a good practice in Ruby
    - Also similar to Pascal's distinction between procedures and functions
    - Javascript event loop
    - Elm's patterns - you don't change state, you just return a command about how it should change
