# Lets Get Loopy!

## Generic Loop
i = 0
loop do 
  puts "i is #{i}"
   i += 1
  break if i == 10
end
  - i is 0 i is 1 - i is 9

## While Loop
i = 0
while i < 10 do
  puts "i is #{i}"
  i += 1
end
  - i is 0 i is 1 - i is 9


puts "Will you do the dishes?"
while gets.chomp != "yes" do
  puts "Will you do the dishes?"
end
  - "Will you do the dishes?" no "Will you do the dishes?" no "Will you do the dishes?" yes

## Until Loop
until i == 10 do
  puts "i is #{i}"
  i += 1
end
  - i is 0 i is 1 - i is 9

## Ranges
(1..10) 
  - 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 
  - inclusive range

(1...10) 
  - 1, 2, 3, 4, 5, 6, 7, 8, 9 
  - exclusive range

('a'..'z') 
  - a-z 
  - inclusive range

## For Loop
for i in 0..10
  puts "#{i} zombies incoming!"
end
- 0 zombies incoming! - 10 zombies incoming!

## Times Loop
5.times do
  puts "Hello World!"
end
- Hello World! 
- Hello World! 
- Hello World! 
- Hello World! 
- Hello World!