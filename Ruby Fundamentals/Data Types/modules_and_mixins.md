# Modules and Mixins

- Modules serve as containers to group related methods, classes, and constants together 
  - Great for code organization and readability and great for sharing code among between classes

module example:
```
module Math
  def self.square(x)
    x * x
  end
end

puts Math.square(2) # => 4
```

In the example above, the Math module contains a self.square method meaning we can call this method directly on the Math module

now example of a module that is included in a class:
```
module Math
  def square(x)
    x * x
  end
end

class Book
  include Math

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

puts book.square(2) # => 4
```

In the example above, the Math module is included in the Book class which lets us call the square method on an instance of the Book class

now an example of a module that is extended in a class:
```
module Math
  def square(x)
    x * x
  end
end

class Book
  extend Math

  attr_accessor :title, :author, :pages

  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages
  end
end

puts Book.square(2) # => 4
```

In this last example, the Math module is extended in the Book class which lets us call the square method directly on the Book class itself

## What's the difference between classes and modules?

Classes are used to create objects, while modules serve to group related methods, classes, and constants together

## When do you use a class and when do you use a module?

- A class when creating objects 
- A module when organizing related methods, classes, or constants

- Modules are beneficial for code grouping and sharing among classes, especially when abstracting logic to enable code sharing