# What is Databinding?

It is the communication between the component's TypeScript code "business logic" and the template "HTML"

## Output Data

We can send data from our TypeScript code to the template. `TypeScript Code ----> Template`

- this can be done with string interpolation `{{data}}` if we jsut want to output data
- there is also property binding `[property] = "data"`

# Reacting to User/Events

When we do event binding like listening to a button click or something on our page, we can make the web page react when the user does something.

## Combining both directions

Two-way binding is where we are outputting/sending data and reacting to events at the same time
