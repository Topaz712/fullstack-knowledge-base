# Hashes

## Creating Hashes
```
my_hash = {
  "This is a key" => "This is a value",
:name => 'Topaz',
'array' => [1,2,3]
}
```

my_hash = Hash.new 
  - {}

## Accessing Values
```
shoes = {
  'summer' => 'sandals',
  'winter' => 'boots'
}
```
- puts shoes['hiking']
  - not found / nil
- puts shoes.fetch('summer')
  - 'sandals'
- puts shoes.fetch('hiking', 'hiking boots')
  - 'hiking boots'
  - added a key and value pair to hash

## Adding and Changing Data
- puts shoes['fall'] = 'sneakers'
- puts shoes['summer'] = 'flip-flops'
  - edit data
- puts shoes
  - shoes = { 'summer' => 'flip-flops', 'winter' => 'boots', 'fall' => 'sneakers'}

## Removing Data
shoes.delete('summer')
puts shoes
  - shoes = { 'winter' => 'boots', 'fall' => 'sneakers'}

## Methods
```
books = {
  'Harry Potter' => 'JK Rowling',
  'Tom Sawyer' => 'Mark Twain',
}
```
- puts books.keys
  - 'Harry Potter' 'Tom Sawyer'
- puts books.values
  - 'JK Rowling' 'Mark Twain'

## Merging Two Hashes
hash1 = { 'a' => 100, 'b' => 200}
hash2 = { 'c' => 300, 'd' => 400}

puts hash1.merge(hash2)
  - { 'a' => 100, 'b' => 200, 'c' => 300, 'd' => 400}
  - order matters

## Symbol as Hash Keys
```
american_cars = {
  :chevy => "Corvette",
  :ford => 'Mustang',
  :dodge => 'Challenger'
}
```

```
japanese_cars = {
  honda: "Accord",
  toyota: 'Tacoma',
  nissan: 'Altima'
}
```
- they way japanese_cars object is written is the typical way to type symbols for hash/cleaner way to type symbols 
-both representations are how symbols are written in hash but how you call them is always the same which is the standard symbol syntax


puts american_cars[:ford]
  - 'Mustang'
puts japanese_cars[:toyota]
  - 'Tacoma'
