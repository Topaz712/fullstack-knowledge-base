# Class methods and class variables

Class methods are methods defined within a class that can be called directly on the class itself

example of a class method:
```
class Book
  @@count = 0

  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages

    @@count += 1
  end

  def self.count
    @@count
  end
end

book1 = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

book2 = Book.new("The Pragmatic Programmer 2", "Andy Hunt and Dave Thomas", 352)

puts Book.count # => 2
```

In this example, 
the Book class has a class method count, accessible directly on the class 

The method uses a class variable `@@count` to keep track of the number of books created 

The **@@ symbol defines class variables**, which can be accessed by all class methods within the class 

The count method helps retrieve the total count of books created

## Self keyword for class and instance methods


The self keyword is versatile, applying to both class and instance methods 

example the of using self in a class method:
```
class User

  def self.say_hello
    puts "Hello"
  end
end

User.say_hello # => Hello
```

- In class methods, `self` refers to the class itself, as shown above in the `say_hello` class method of the User class 

example of using self in an instance method:
```
class User
  def initialize(name)
    @name = name
  end

  def say_hello
    puts "Hello, my name is #{self.name}"
  end

  def name
    @name
  end
end

user = User.new("Alice")

user.say_hello # => Hello, my name is Alice
```

- In instance methods, `self` refers to the instance the method is called on, facilitating access to instance variables, as shown in the `say_hello` instance method of the User class
  - In short, we can call the say_hello method on the User class