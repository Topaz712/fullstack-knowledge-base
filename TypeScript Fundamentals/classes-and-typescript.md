# Classes and TypeScript

## Classes

- With classes we can define blueprints for objects we plan to instantiate

```class Student {
  firstName: string;
  lastName: string;
  age: number;
  courses: string[];

  constructor(first: string, last: string, age: number, courses: string[]) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.course = courses;
  }

  enroll(courseName: string) {
    this.courses.push(courseName);
  }
}
```

by adding a constructor method to this class we can then define the default method that will be called when we instantiate a new object based on that class.
we have the same argument names as we have the properties so we can just set `firstName` equal to `first` and so on.

by having it set like this we can define a new student by instantiating this student class by passing in these values for our parameters to the constructor function
`const student = new Student('Topacio', 'Z', 150, ['Angular']);`

by adding a method

```enroll(courseName: string) {
  this.courses.push(courseName);
}
```

that is the method shorthand notation, we have the function name, our parameter list, and then the function body, so its basically defined like a regular JavaScript function
Now we can call this method:
`student.enroll('React');` and if we were to call `student.courses` it will inculde both Angular and React

## The difference with JavaScript and TypeScript is in TypeScript classes we can define all those different properties it will have, ahead of time including their types

```class Student {
  firstName: string;
  lastName: string;
  age: number;
  courses: string[];
```

## and in JavaScript we would not have those property assignments, instead properties would be added by setting them in the constructor

```constructor(first: string, last: string, age: number, courses: string[]) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.course = courses;
  }
```

- With TypeScript we can control whether a property or a method should be publicly accessible or if it should be private.

  > Private properties or method can only be used from inside of the class
  > Meanwhile public properties or methods can be accessed outside of the class with the dot notation
  > To make them private just add the private keyword infront of the property defintion

- If we were to make courses private `private courses: string[];` we can add a method to the class `listCourses() { return this.courses.slice();}` this way we return a copy of courses to make sure if someone else would try to push a new element onto the array outside of the class, the original array inside of the class will not be altered.
  > We would get an error if we try to call course like normal `student.courses();` so instead we can now call it like `student.listCourses();` if we want to see all the courses that student is enrolled in.

**Its common practice/pattern in TypeScript to define properties ahead of time and then assign values to those properties in the constructor, not necessary for all the classes we create**

- Since its so common to assign values to those properties ahead of time, we can do it in one step with TypeScript :

  > `constructor(public first: string, public last: string, public age: number, private courses: string[])`

- So _instead of defining our properties at the beginning_ we can simply **add a modifier, the accessor keywords** _infront of our parameters in the constructor method_, just add public/private in front of all the parameters that should be set up as public/private properties

- when done this way, we dont assign values to the constructor the old way instead we do it this way :

````constructor(
    public first: string,
    public last: string,
    public age: number,
    public courses: string[])```
````

> it leads to the same result as before

This is the _shorthand notation_ for defining certain properties of this class, their types, and for letting a user assign values to those properties when the class is instantiated

> Everything should work the same, the only thing that changed was the shorthand notation.
> _That is the classes feature which is also a part of TypeScript_
