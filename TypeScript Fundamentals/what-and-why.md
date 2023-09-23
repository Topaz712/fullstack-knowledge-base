# What is TypeScript?

It's a **programming language that builds upon JavaScript** or also known as extends JavaScript because the **core programming language still is JavaScript.**

- base JavaScript syntax code does not change

- TypeScript adds more features to JS syntax
  > Most importantly, it adds static typing to JS because on its own, JavaScript is dynamically typed

# Why use TypeScript?

**JavaScript knows the concepts of types but because it is dynamically typed**, in a function it does not expect any particular types it just knows that it will recieve parameters and thats it
and since **it is not statically typed**, the types for the function are not announced ahead of time.
instead **it just takes whatever it gets and tries to execute the code.**

> example without TypeScript
> `function add(a, b) {`
> `return a + b;`
> `}`
> `const result = add('2', '5');`
> `console.log(result);`// 25
> _It concatenates two strings because it recieves two strings_

- In a bigger project with lots of code files and potentially alot of people working on the code base you might sometimes call a function or use some object in an unintended way and you can run into problems because nothing is warning you that this is not how you should use a function.

  > example with TypeScript
  > `function add(a: number, b: number) {` >`return a + b;`
  > `}`
  > `const result = add('2', '5');`
  > `console.log(result);`// prints an error
  > _It lets us know the argument of type string is not assignable to a parameter of type number._

- **With TypeScript we can add type annotations** on function parameters but we will also be able to use types in many other situtations as well

- **TypeScript allows us to write better code in the end because we can catch and avoid such errors/unintended use** of a function before running and testing code that we **dont have to track them** down on runtime.
