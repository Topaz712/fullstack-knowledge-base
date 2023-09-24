# Working with Union Types

- If we have a variable where we have more than one type, like if we want to allow two different kinds of objects, this would call for a feature called **union types**

- union type is a type definition which allows more than one type

- we call it by adding a pipe symbol after our first type and we can have as many as we need

  > `let course: string | number = 'React - The Complete Guide';`
  > so now
  > `course = 12341;`
  > will work because we are allowing a number alternatively to a string value

- We can use a union type anywhere where we have a type assignment not just when using a type inference

## Union types are another a key TypeScript feature which allows us to define more flexible values and types.
