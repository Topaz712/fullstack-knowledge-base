## Basic Conditional
a = true
puts "hello" if 4 != 5
  - hello

## If Else/Elseif
a = 3
if a > 3
  puts "#{a} is greater than 3"
elsif a < 3
  puts "#{a} is less than 3"
else 
  puts "#{a} is equal to 3"
end

## Unless Statement
unless a == 3
  puts "#{a} does not equal 3"
end

## Comparison Operators

### == not assigning value, checking for equal value
3 == 3 #=> true
3 == 5 #=> false

### != checking for non equal value
3 != 4 #=> true
3 != 3 #=> false

### > greater than
3 > 2 #=> true
3 > 4 #=> false

### < less than
3 < 2 #=> false
3 < 4 #=> true

### >=
3 >= 2 #=> true
2 >= 3 #=> false

### <=
3 <= 3 #=> true
2 <= 3 #=> true

### <=> spaceship operator
- returns -1 if first argument is less than second argument
- returns 0 if first argument is equal to second argument
- returns 1 if first argument is greater than second argument

puts 4 <=> 3
  - 1

## Logical Operators

### && and
a  = 5
puts "#{a} is between 4 and 10" if a > 4 && a < 10
  - 5 is between 4 and 10

### || or
a  = 5
puts "#{a} is either less than 4 or greater than 10" if a > 4 || a < 10
  - 5 is either less than 4 or greater than 10

a = "this"
puts "#{a} is either equal to this or that" if a == "this" || a == "that"
  - this is either equal to this or that

## Ternary Operator
can_swim = true

response = can_swim ? "You wont drown" : "You might drown"
puts response
  - You wont drown

## Case Statement
grade = 'A'

case grade
  when "A"
    puts "Good Job!"
  when "B"
    puts "Great Job, try better next time though"
  when "C"
    puts "You still passed, but study a bit"
  when "D"
    puts "Almost Passed, study up"
  when "F"
    puts "You failed, Please study"
end
  - Good Job!