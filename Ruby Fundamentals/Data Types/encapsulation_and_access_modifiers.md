# Encapsulation and Access Modifiers


**Encapsulation is the process of  concealing the internal details of an object, allowing access only through a clearly defined interface** 
  - *It ensures that an object's internal details remain hidden*

here's an example:
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

book = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

book.print_title # => The Pragmatic Programmer

book.print_author # => Andy Hunt and Dave Thomas

book.print_pages # => 352
```
- In this encapsulation example, the Book class has private instance variables @title, @author, and @pages, accessed only through instance methods 

- This hides internal details, allowing changes without impacting external code 

- Access modifiers like public, protected, and private are keywords used to control visibility: 
  - public methods and variables for universal access 
  - protected methods and variables limited to the defining class and its subclasses
  - private methods and variables restricted to the class that defines them

this is an example of access modifiers through public methods and private:
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

def print_details
    puts @title
    puts @author
    puts @pages
  end

private
  def print_details_private
    puts @title
    puts @author
    puts @pages
  end
end

book = Book.new("The Pragmatic Programmer", "Andy Hunt and Dave Thomas", 352)

book.print_title # => The Pragmatic Programmer

book.print_author # => Andy Hunt and Dave Thomas

book.print_pages # => 352

book.print_details # => The Pragmatic Programmer
                    #    Andy Hunt and Dave Thomas
                    #    352


book.print_details_private # => NoMethodError: private method `print_details_private' called for #<Book:0x00007f8b9a8b6a10>
```
In this example, 
the Book class has public method `print_details` accessible by anyone, printing title, author, and pages 

The private method `print_details_private` can only be accessed within the class that defines it

an example of private methods through inheritance:
```
class Animal
  def initialize(name)
    @name = name
  end

  def print_details
     puts @name
  end

  private

  def print_details_private
    puts @name
  end
end

class Dog < Animal
end

animal = Animal.new("animal")

animal.print_details # => animal


animal.print_details_private # => NoMethodError: private method `print_details_private' called for #<Animal:0x00007f8b9a8b6a10>

dog = Dog.new("dog")

dog.print_details # => dog


dog.print_details_private # => NoMethodError: private method `print_details_private' called for #<Dog:0x00007f8b9a8b6a10>
```

## Practice Problem

Create a Ruby program that performs the following tasks using encapsulation and access modifiers that includes public and private methods:

1. Define a class called Vehicle that takes a make and model as arguments
```
class Vehicle
  def initialize(make, model)
    @make = make
    @model = model
  end
```

2. Define a method called print_make that prints the make of the car
```
  def print_make
    puts @make
  end
```

3. Define a method called print_model that prints the model of the car
```
  def print_model
    puts @model
  end
```
4. Define a method called print_details that prints the make and model of the car 
```
  def print_details
    puts @make
    puts @model
  end
```
private method: 
```
  private
    def print_details_private
      puts @make
      puts @model
    end
  end

```

5. Define a class called Car that inherits from the Vehicle class 
```
class Car < Vehicle
end
```
notes answer is this now becuase of question 6:
```
class Car < Vehicle
  def initialize(make, model, year)
    super(make, model)
    @year = year
end
```

6. Define a method called print_details that prints the make, model, and year of the car
```
  def print_details
    puts @make
    puts @model
    puts @year
  end
end
```

7. Define a class called Motorcycle that inherits from the Vehicle class

```
class Motorcycle < Vehicle
end
```