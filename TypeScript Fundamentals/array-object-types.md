# Array and Object Types

## More complex types

## Arrays

- `let hobbies: string;`
  > If I want to use hobbies to store an array of strings then this is code is wrong because it will only let us store a single string, so instead we will use:
- `let hobbies: string[];`
  `hobbies = ['Sports', 'Cooking'];`
  > In TypeScript this allows us to store an array of strings
- In the array of strings if i add something like a number then it will give an error because this hobbies variable is annotated with type string so it will only contain strings

## Objects

- `let person;`
  `person = {`
  `name: 'Topaz',`
  `age: 32`
  `};`

  > by default it will let us store any type to person if left as is but we shouldn't use this because it is a fallback type which defeats the entire purpose of using TypeScript

`let person: {};`

- Notice this is not on the right side of an equal sign so we are not creating an object instead its in the place we set for a type of a variable

  > We're using a TypeScript feature which is the object type definition

- so for example we will define the structure of an object like so:
  `let person: {`
  `name: string;`
  `age: number;`
  `}`

  > This is telling TypeScript that only objects that have these types should be stored in this variable

## Arrays and Objects can also be combined

- We can have an array full of people by setting the type-of people to the object type but as an array by adding sqaure brackets after, like so:

`let people: {`
`name: string;`
`age: number;`
`}[];`

**This is how we can get a bit more advanced, by combining the different TypeScript features and by combining different types**
