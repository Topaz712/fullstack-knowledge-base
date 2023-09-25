# Understanding Generics

## Generics is a slightly more advanced but very important TypeScript feature

`function insertAtBeginning(array: any[], value: any) { const newArray = [value, ...array]; return newArray; }`

That can be a utility helper function which we create to have a function which we can easily call to add a value in an array without changing the existing array.

> The advantage of this function could be that the original array never changes but instead we're getting a brand new array.

`const demoArray = [1, 2, 3];`
`const updatedArray = insertAtBeginning(demoArray, -1);`//[-1, 1, 2, 3]
With this, we will know that the updatedArray will be demoArray, with minus one inserted at the beginning

**The only problem is** that the _updatedArray is infered_ to be of **any kind** of objects or any kind of values and **that's not useful** _because it removes all kind of TypeScript support we might be getting after calling this function._

`updatedArray[0].split('');`

- If we try to access the first element and call split here which we can call on a string
- We wont get an error but we'd get a runtime error instead because we can't call split on a number, but TypeScript doesn't know that the first value in updatedArray is a number
  > we know it but TypeScript doesnt because we set type to "any" in the parameters

We can work around this problem by converting the function with the generics feature

- We will use a special syntax, after the function name, before the parameters list, we add angle brackets <>

  > this is not a standard JavaScript feature, it's only a feature we can use here since we're using TypeScript "in .ts file"

- So _inside the brackets_ we can _define a generic type_ which **will only be availble in the function**
  > usually its T for type but any identifier of choice is okay too, and now we can use this type in our function, even the parameters list

`function insertAtBeginning<T>(array: T[], value: T) { const newArray = [value, ...array]; return newArray; }`

Now when we call this function:
`const updatedArray = insertAtBeginning(demoArray, -1);`
TypeScript should look at the concrete values of the arguments
(`demoArray`, -1); and it understands that this is an array of numbers, and that the `-1` is just a number
Therefore TypeScript understands that the `updatedArray` will be an array of numbers because of the **generic type feature** because in `array: T[], value: T` we are actually telling TypeScript that **the type in there is actually not any type or any kind of value.** Instead we tell it that they type of the array and of the value should be the same, even though its an array full of the same types of values that the single value has.
so it will infer a type

## The important feature of type generics is that it helps write "functions in this case" which are flexible yet type safe.

## Flexibility and type safety is what we get using type generics

> _although they are flexible and work with any type, once a certain type is used for that function execution, that type will be locked and known_ --> **inferred**
