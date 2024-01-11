## Classes and Objects

Create a Ruby program that performs the following tasks using classes and objects:

1. Define a class called 'Car' that takes a make and model as arguments
```
class Car
  def initialize(make, model, color)
  @make = make
  @model = model
  @color = color
end
```

2. Define a method called 'print_color' that prints the color of the car
```
  def print_color
    puts @color
  end
end
```

3. Create an instance of the 'Car' class called 'car'
```
car = Car.new('car')
```

4. Create a test for the 'Car' class that tests the 'print_color' method
```
require 'rspec'

require_relative '../car'

describe Car do
  describle '#print_color' do
    it 'returns the color of the car' do
      car = Car.new("car")

      expect(car.print_color).to eq("blue")
```

solution given:
```
class Car
  def initialize(color)
    @color = color
  end

  def print_color
    @color
  end
end
```

## Inheritance

Create a Ruby program that performs the following tasks using inheritance:

1. Define a class called 'Fruit' that takes a name as an argument
```
class Fruit
  def initialize(name)
    @name = name
end
```

2. Define a method called 'print_name' that prints the name of the fruit
```
def print_name
  puts @name
end
```

3. Define a class called 'Apple' that inherits from the 'Fruit' class
```
class Apple < Fruit
end
```

4. Create an instance of the 'Apple' class called 'apple'
```
apple = Apple.new('apple')
```

5. Create a test for the 'Apple' class that tests the 'print_name' method
```
require 'rspec'

require_relative '../apple'

describe Apple do
  describle '#print_name' do
    it 'prints the name of the fruit' do
      apple = Apple.new("apple")

      expect(apple.print_name).to eq("apple")
    end
  end
end
```

## Exercise: Enhanced Car Management System

In this exercise, you will create a more complex Ruby program involving the Car class. This program will not only handle car properties but also include a collection of cars and perform various operations using built-in array methods.

### Define a Car class:

1. The class should initialize with a make, model, and color. Include methods to get and set each of these attributes
```
class Car
  attr_accessor :make, :model, :color

  def initialize(make, model, color)
    @make = make
    @model = model
    @color = color
  end
```

2. Add a method info that returns a string with all the car's details
```
  def print_details
    "Make: #{@make}, Model: #{@model}, Color: #{@color}"
  end
end
```

### Create a Garage class:

1. This class will manage a collection of Car objects
```
class Garage
  def initialize
    @cars = []
end
```

2. Implement methods to add a car, remove a car by make and model, and list all cars
```
  def add_car(car)
    @cars << car
  end

  def remove_car(car)
    @cars.delete_if { |car| car.make == make && car.model == model }
  end

  def list_cars
    @cars.map(&:info)
  end
```

3. Add a method to find all cars of a specific color
```
  def find_cars_by_color(color)
    @cars.select { |car| car.color == color }.map(&:info)
  end
end
```

4. add a method to clear all cars from the garage
```
  def clear_all_cars
    @cars = []
  end
end
```


Write tests for both classes:

solution given for car_spec.rb:
```
require 'rspec'
require_relative '../car'

describe Car do
  car = Car.new("Toyota", "Corolla", "Blue")

  it 'should return correct make' do
    expect(car.make).to eq("Toyota")
  end

  it 'should return correct model' do
    expect(car.model).to eq("Corolla")
  end

  it 'should return correct color' do
    expect(car.color).to eq("Blue")
  end

  it 'should return correct info' do
    expect(car.info).to eq("Make: Toyota, Model: Corolla, Color: Blue")
  end

end
```

solution given for garage_spec.rb
```
require 'rspec'
require_relative '../car'
require_relative '../garage'

describe Garage do
  let(:car1) { Car.new("Toyota", "Corolla", "Blue") }
  let(:car2) { Car.new("Honda", "Civic", "Red") }

  before(:each) do
    Garage.add_car(car1)
    Garage.add_car(car2)
  end

  after(:each) do
    Garage.clear_cars
  end

  it 'should list all cars' do
    expect(Garage.list_cars).to eq([car1.info, car2.info])
  end

  it 'should find cars by color' do
    expect(Garage.find_cars_by_color("Red")).to eq([car2.info])
  end

  it 'should remove a car' do
    Garage.remove_car("Toyota", "Corolla")
    expect(Garage.list_cars).not_to include(car1.info)
  end
end

```
Test all the functionalities of the Car and Garage classes.