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

