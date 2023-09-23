# Type Inference

When going over the TypeScript code the first step was to declare a variable with a type assigned and then the second step a value is set

In usual JavaScript code we declare a variable and then immediately assign an initial value.

- With type inference if I have code like this:
  `let course = 'React- The Complete Guide';`
  `course = 12341;`
  > By default TypeScript tries to infer as many types as possible without me explicitly stating the type
- Although if i wanted to add the type for it to say `let course: string = 'React- The Complete Guide';` _I could because its not wrong_, **but it would be redundant**

- Once you immediatly initialize a variable with a type, like the first code example. TypeScript will look at the type and see that the type string was stored in the variable and will then use that value type as an inferred type for that variable
- so if you try to reassign that variable later with another type, an error will show because of type inference
  > **It is considered good practice and idea to embrace that type inference feature and not unnecessarily specify the type in addition**
