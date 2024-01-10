# Polymorphism

Polymorphism is the ability of an object to take various forms, allowing the object to respond to the same method in diffirent ways

this is an example of it:
```
class Animal
  def speak
    puts "I am an animal"
  end
end

class Dog < Animal
  def speak
    puts "I am a dog"
  end
end

class Cat < Animal
  def speak
    puts "I am a cat"
  end
end

def speak(animal)
  animal.speak
end

animal = Animal.new

speak(animal) # => I am an animal

dog = Dog.new

speak(dog) # => I am a dog

cat = Cat.new

speak(cat) # => I am a cat
```

- This example demonstrates polymorphism using classes Animal, Dog, and Cat
  - Each class has a 'speak' method, responding differently to the same message 
  - The 'speak' function can handle various objects, enabling code to work with different types of animals
  
**Polymorphism allows flexibility in writing code that can seamlessly adapt to diverse object types**