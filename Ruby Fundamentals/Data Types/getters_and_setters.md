# Getters and Setters

**Getters and setters are methods that are used to get and set the value of instance variables**

example of it: 
```
class Book
  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages
  end

  def title
    @title
  end

  def title=(title)
    @title = title
  end

  def author
    @author
  end

  def author=(author)
    @author = author
  end

  def pages
    @pages
  end

  def pages=(pages)
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
the Book class has getters and setters for instance variables like @title, @author, @pages 

***Getters retrieve values, and setters modify values ***

This lets us access and update the instance variables in a controlled manner using their defined methods






