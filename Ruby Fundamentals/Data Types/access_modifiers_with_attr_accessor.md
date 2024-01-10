# Accessing modifiers with attr_accessor

The `attr_accessor` and `attr_reader` methods are used to define getters and setters for instance variables 

- `attr_accessor` sets up both getters and setters 
- `attr_reader` only sets up getters for instance variables

an example of using attr_accessor and attr_reader:
```
class Book
  attr_accessor :title, :author, :pages

  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages
  end
end

book = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

puts book.title # => The Pragmatic Programmer

puts book.author # => Andy Hunt and Dave Thomas

puts book.pages # => 352

book.title = "The Pragmatic Programmer 2"

puts book.title # => The Pragmatic Programmer 2
```
In this example, 
the `attr_accessor` method is is used to define getters and setters for instance variables like `:title, :author, :pages` 

This makes the code simpler by letting us easily access and change the values of variables in our object and don't have to explicitly define separate methods for each variable