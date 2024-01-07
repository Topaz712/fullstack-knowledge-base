1. Variables
- Create a Ruby script that declares a local variable called my_name and assigns it your full name as a string
```
my_name = "Topaz Z"
puts my_name
# Topaz Z
```

2. Arithmetic Operators
- Create a Ruby script that calculates and prints the area of a rectangle with a width of 10 and a height of 5
```
width = 10
height = 5
area = width * height
puts area
# 50
```

3. Conditional Operators & Control Flow
- Create a Ruby script that checks if a number is positive, negative, or zero. If it is a positive number, print "positive". If it is a negative number, print "negative". Otherwise, print "zero"
```
def num(number)
if number > 0 
  puts "#{number} is positive"
  elsif number < 0
    puts "#{number} is negative"
  else 
    puts "Zero"
  end 
end
num(2)
# 2 is positive
```
```
number = 0
if number > 0 
    puts "#{number} is positive"
  elsif number < 0
    puts "#{number} is negative"
  else 
    puts "Zero"
end 
# Zero
```
4. Basic Methods
- Create a Ruby script that defines a method called add that takes two numbers as arguments and returns their sum
```
def add(a, b)
  puts a + b
end
add(2, 9)
# 11
```

5. Testing with RSpec
### setting up Rspec
  - in gem file, under # gem "rails", add gem 'rspec'
  - then in shell run commands =
    - gem install rspec (installs rspec)
    - bundle install (installs all the gems in your Gemfile)
    - rspec --init (creates the necessary config files)
now we can create a test tile and name such as math_operations_spec.rb in spec directory
  - when ready to test type rspec 

- Create a test for a method that takes two numbers as arguments and returns their multiplication. Run the tests and make sure they pass
```
def multiply(a, b)
  a * b
end

require_relative '../math_operations'
describe 'math_operations' do
  describe '#multipy' do
    it 'correctly multiplies two numbers' do
      expect(muliply(2, 9)).to eq(18)
    end
  end
end
```

6. Arrays
- Create a Ruby script that iterates over the array [1, 2, 3, 4, 5] and prints each element
```
[1, 2, 3, 4, 5].each do |number|
  puts number
end
# 1 - 5
```

7. Hashes
- Create a Ruby script that iterates over the hash { "name" => "Alice", "age" => 30 } and prints each key-value pair
```
{ "name" => "Alice", "age" => 30 }.each do |key, value|
  puts "#{key}: #{value}"
end
# name: Alice age: 30
```

8. Loops & Control Flow
- Create a Ruby script that prints the numbers from 1 to 20. For multiples of three, print "Fizz" instead of the number. For multiples of five, print "Buzz". For numbers that are multiples of both three and five, print "FizzBuzz"
```
num = 0
while num < 20
  num += 1
  if num % 3 == 0 && num % 5 == 0
    puts "FizzBuzz"
  elsif num % 3 == 0
    puts "Fizz"
  elsif num % 5 == 0
    puts "Buzz"
  else
    puts num
  end
end
# 1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz 16 17 Fizz 19 Buzz
```
```
(1..20).each do |num|
  if num % 3 == 0 && num % 5 == 0
    puts "FizzBuzz"
  elsif num % 3 == 0
    puts "Fizz"
  elsif num % 5 == 0
    puts "Buzz"
  else
    puts num
  end
end
# 1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz 16 17 Fizz 19 Buzz
```

9. Super Fizz Buzz
- Create a Ruby script that prints the numbers from 1 to 100. For multiples of three, print "Fizz" instead of the number. For multiples of five, print "Buzz". For numbers that are multiples of both three and five, print "FizzBuzz". For numbers that are multiples of seven, print "Super". For numbers that are multiples of both three and seven, print "FizzSuper". For numbers that are multiples of both five and seven, print "BuzzSuper". For numbers that are multiples of three, five, and seven, print "FizzBuzzSuper"

```
(0..100).each do |num|
  if num % 3 == 0 && num % 5 == 0 && num % 7 == 0
    puts "FizzBuzzSuper"
  elsif num % 3 == 0 && num % 7 == 0
    puts "FizzSuper"
  elsif num % 3 == 0 && num % 5 == 0
    puts "FizzBuzz"
  elsif num % 3 == 0
    puts "Fizz"
  elsif num % 5 == 0
    puts "Buzz"
  elsif num % 7 == 0
    puts "Super"
  else
    puts num
  end
end
# FizzBuzzSuper 1 2 Fizz 4 Buzz Fizz Super 8 Fizz Buzz 11 Fizz 13 Super FizzBuzz 16 17 Fizz 19 Buzz FizzSuper 22 23 Fizz Buzz 26 Fizz Super 29 FizzBuzz 31 32 Fizz 34 Buzz Fizz 37 38 Fizz Buzz 41 FizzSuper 43 44 FizzBuzz 46 47 Fizz Super Buzz Fizz 52 53 Fizz Buzz Super Fizz 58 59 FizzBuzz 61 62 FizzSuper 64 Buzz Fizz 67 68 Fizz Buzz 71 Fizz 73 74 FizzBuzz 76 Super Fizz 79 Buzz Fizz 82 83 FizzSuper Buzz 86 Fizz 88 89 FizzBuzz Super 92 Fizz 94 Buzz Fizz 97 Super Fizz Buzz
```