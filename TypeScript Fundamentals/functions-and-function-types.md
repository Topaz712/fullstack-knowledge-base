# Diving into Functions and Function Types

functions combines with types and generic types

## Functions and types

`function add(a: number, b: number) { return a + b; }`

> type inference happens here with the return value, it infers a number will be the returned value because it sees the code in return and with the parameters of only type number

but we can set the return type of a function by adding a colon after the function parameter list like so: `(a: number, b: number): number {`

- We can set the return value to a number or a string or even a union type would also be possible.
  > but if thats the type we want to stick with, then we dont have a reason to explicitly define it ourselves because TypeScript already infers type

Keep in mind that with functions, when we work with types, we dont just use types for the parameters but also the return value

> Not only do functions have input but also output, hence the return type.

A special return type worth noting is void :

`function print(value: any) { console.log(value); }`//void

The function above won't return anything because it has no return statement therefore its special return type is void

- void is comparable to null and undefined but its only used in conjuction with functions and means that the function will never return
  > if you want to work with the returned value of that function, you will work with undefined

Naming a funtion print will give an error because JavaScript has a built in "print" function and it will clash, so when trying to compile that TypeScript file it will give an error
