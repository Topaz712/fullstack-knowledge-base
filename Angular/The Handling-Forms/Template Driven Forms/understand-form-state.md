# TD: Understanding Form State

In the previous lecture, we learned how to submit an Angular created form and access the object that Angular generates for us

This object had some interesting properties when we looked at the value property it in the console and so the _value property stores user input in key-value pairs_ which lets us understand the state of our form and we can see which controls we registered on the controls object

The _controls object, lists the registered controls like email, secret, or username, each of type form control_

Some of these control properties include _"Dirty" - when changes are made_, "Disabled", "Enabled", "Errors", "Invalid", "Valid", and "Touched"

Dirty - True when the form is changed, and false when not

Disabled - True when the form is disabled

Invalid - False by default; it becomes true if validators are added

Touched - Indicates if a field was clicked, differentiating it from "Dirty"

These properties help manage a user's experience, like disabling the submit button when the form is invalid

Max emphasizes that it's important to explore and understand these properties and how they can be used to enhance our application
