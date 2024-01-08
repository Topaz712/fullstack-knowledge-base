# Understanding Classes and Objects

## Object Oriented Programming

- Object-oriented programming (OOP) uses objects and classes, Objects hold data and procedures, while classes are blueprints for creating objects 
- In OOP, programs are built by making objects interact 
- Ruby is an OOP language where everything is as an object

- OOP is valuable because it makes programs easier to understand, modify, and maintain, also it promotes flexibility and reusability in creating programs

## Classes and Objects

- A class is a blueprint for creating objects,  it defines properties and behaviors of an object 

- Classes group methods and variables for easier use, acting like factories that produce objects, this avoids repetitive code writing 
- For example, a Book class could manage books in a program, creating instances for each book with unique properties like *title, author, pages, and methods like printing details*

**An object is an instance of a class. Instances are often called objects because they are instances of a class**

- When creating a class in Ruby we use the **PascalCase**, which is *capatalizing the first letter of each word in the name in the class*
```
class Book
end
```

- In Ruby, to make an instance of a class, we use the *'new' method*, it's a method defined in the *Class* class, which generates a new instance of the class it's applied to
```
book = Book.new
```

- In Ruby, we define methods using **def** followed by the method name in **snake_case** which the words in the name of the method are separated by underscores
  - These methods, called instance methods, are part of a class and work with instances of that class

- Instance variables, marked with '@' are accessible to all instance methods in a class

- The **initialize method** is a special constructor method in Ruby because it's used to construct or create an instance of a class
  - It initializes instance variables when a class instance is created, and we can pass arguments to it during the instance creation 
  - This method is crucial for setting up or constructing instances of a class
```
class Book
  def initialize(title, author, pages)
    @title = title
    @author = author
    @pages = pages
  end

  def print_title
    puts @title
  end

  def print_author
    puts @author
  end

  def print_pages
    puts @pages
  end
end
```

- To see it how it works, we create an instance of the Book class and call the instance methods
```
book = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

book.print_title # => The Pragmatic Programmer

book.print_author # => Andy Hunt and Dave Thomas

book.print_pages # => 352

```

## Practice Problem
Create a Ruby program that performs the following tasks using classes and objects:

- Define a class called 'Animal' that takes a name as an argument.
```
class Animal
  def initialize(name)
  @name = name
end
```

- Define a method called 'speak' that prints the name of the animal.
```
def speak
  puts @name
end
```

- Create an instance of the Animal class called 'dog'.
```
dog = Animal.new("Bartholomew")
```

- Call the 'speak' method on the 'dog' instance.
```
dog.speak
# Bartholomew
```