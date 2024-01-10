# Inheritance

- Inheritance is a mechanism that lets us create a class based on another class 

- The original class is the superclass or parent class, and the new one is the subclass or child class

- Inheritance is useful for code to be reuse, enabling the subclass to inherit properties and behaviors from the superclass which helps avoid repetitive coding

This code defines two classes: Item and Book:
```
class Item
  def initialize(name, price)
    @name = name
    @price = price
  end

  def print_name
    puts @name
  end

  def print_price
    puts @price
  end
end

class Book < Item
  def initialize(name, price, author, pages)
    super(name, price)
    @author = author
    @pages = pages
  end

  def print_author
    puts @author
  end

  def print_pages
    puts @pages
  end
end
```
- The Book class inherits from the Item class, all of its properties and behaviors 
  - This inheritance helps avoid repetitive code 
- The **super** keyword is used in the Book class to invoke the same named method from the *superclass Item*, allowing for the reuse of common functionality

instance creation of the Book class and calling the instance methods:
```
book = Book.new("The Pragmatic Programmer", 29.95, "Andy Hunt and Dave Thomas", 352)

book.print_name # => The Pragmatic Programmer

book.print_price # => 29.95

book.print_author # => Andy Hunt and Dave Thomas

book.print_pages # => 352
```

## Practice Problem

Create a Ruby program that performs the following tasks using inheritance:

1. Define a class called 'Animal' that takes a name as an argument
```
class Animal
  def initialization(name)
  @name = name
end
```

2. Define a method called 'speak' that prints the name of the animal
```
  def speak
    puts @name
  end
end
```

3. Define a class called 'Dog' that inherits from the 'Animal' class.
Create an instance of the 'Dog' class called 'dog'
```
class Dog < Animal
end

dog = Dog.new("Blossom")
```

4. Call the 'speak' method on the 'dog' instance
```
dog.speak # Blossom
```

5. Define a class called 'Cat' that inherits from the 'Animal' class
```
class Cat < Animal
end
```

6. Create an instance of the 'Cat' class called 'cat'
```
cat = Cat.new("Bubbles")
```

7. Call the 'speak' method on the 'cat' instance
```
cat.speak # Bubbles
```