# Working with Interfaces

- The interface feature is _similar to classes and objects in general_
  > It is a feature that **only exists in TypeScript**, not in vanilla JavaScript or any interface code we write, therefor it will not compile.

**Interface features in their most basic form are really just objest type defintions**

So we can use interfaces to define object types

```Interface Human {
  firstName: string;
  age: number;

  greet: () => void;
}

let Topaz: Human;

Topaz = {
  firstName: 'Topacio',
  age: 150,
  greet() {
    console.log('Hello!');
  },
};
```

as well as type keyword to create an alias which is just like so: `type Human = {` and it would work as well

## So are there interfaces when we can do the same with the type keyword?

When we want to define object types we can use interfaces as an alternative to the type keyword but there is an extra feature that the type keyword doesnt give us.

- _interfaces can be implemented by classes_, and when they are, _they force classes to have a structure defined_ by the interface.
  _This is helpful when building an application with multiple developers_ and we want to ensure that a certain class written by another developer has a certain structure because for us for a part we're working on, need that class to have that structure , like if we need that class to have a certain method and its the same for Angular

- Angular also has a couple of interfaces we will use from time to time, which will then force us to add certain features to the classes we define so in turn it can use these classes correctly internally.
  > will be working with alot of classes with Angular

```class Instructor implements Human {
  firstName: string;
  age: number;
  greet() {
    console.log('Hello!!!!');
  }
}
```

**A key part of interfaces is that they dont just act as object types, they also force us to set up a certain structure for our classes.**
