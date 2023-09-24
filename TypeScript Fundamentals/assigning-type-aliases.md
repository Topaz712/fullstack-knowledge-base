# Assigning Type Aliases

- With type alias we can define our own base type in which a more complex definition is stored

  > Then we can use type alias instead of repeating the entire type definitions.

- **for example: instead of**

  > `let person: {name: string; age: number; };`
  > and
  > `let people: { name: string; age: number; };`

- We will **define** such a **type alias** with the **type keyword**
  > _it is a keyword that does not exist in standard JavaScript but in which is added by TypeScript instead_

To use it we will use type keyword along with any name of choice and it will be our new type name.

- For example:

  > `type Person = {name: string; age: number;};`

- After the equal sign we have a type defintion because this is a pure TypeScript feature.
  > this will basically be thrown out the window when the code is compiled to JavaScript because on the right side of the equal sign it is not a JavaScript value, but instead a type defintion.

We can use our alias instead now in all the places where we used the object type like person and people

- It is still the same type but it only needs to be defined once and it can be repeated in all the places we need it like:
  > `let person: Person;` or `let people = Person[];`
  > It can be used normally or with an array of persons

**In conclusion this _type aliases_ is a very important feature , which can _save us on alot of typing code_ which in turn makes our _code more concise_ and _easier to maintain_.**
