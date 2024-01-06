# Arrays

## Creating Arrays
str_array = ['a', 'b', 'c']

- Array.new()  
  - []
- Array.new(3)  
  - [3]
- Array.new(3, 9)  
  - [9, 9, 9]
- Array.new(5, true) 
  - [true, true, true, true, true]


## Accessing Elemets
- str_array = ['a', 'b', 'c']
- str_array[0] 
  - 'a'
- str_array[-2] 
  - 'b'
- str_array.first(2) 
  - ['a', 'b']
- str_array.last(2) 
  - ['c', 'b']


## Adding and Subtracting Elements
- num_array = [1, 2, 3]
- num_array.shift 
  - [2, 3]
- num_array.unshift(1) 
  - [1, 2, 3]

- num_array.push(4, 5) 
  - adds to end of index
  - [1, 2, 3, 4, 5]
- num_array << 6 
  - shovel operator, adds to end
  - [1, 2, 3, 4, 5, 6]
- num_array.pop 
  - 6 
  - removes last element index
- num_array 
  - [1, 2, 3, 4, 5]

## Adding and Subtracting Arrays
a = [1, 2, 3]
b = [4, 5, 6]

- a + b 
  - [1, 2, 3, 4, 5, 6]
- a.concat(b) 
  - [1, 2, 3, 4, 5, 6]
- [1, 1, 1, 1, 2, 3, 4] - [1, 4] 
  - [2, 3]

## Basic Array methods
- [[]].empty? 
  - false
- [].empty? 
  - true
- [1, 2].empty? 
  - false

- [1, 2, 3].length 
  - 3
- [1, 2, 3].reverse 
  - [3, 2, 1]
- [1, 2, 3].include?(3) 
  - true
- [1, 2, 3].include?("3") 
  - false

- "Hi how are you".split(" ") 
  - ["Hi", "how", "are", "you"]
- [1, 2, 3].join('-') 
  - '"1-2-3"'