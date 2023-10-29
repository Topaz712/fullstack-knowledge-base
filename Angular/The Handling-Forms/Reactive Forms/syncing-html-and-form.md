# Reactive: Syncing HTML and Form

In this lesson, Max shows us how synchronizing the form created in TypeScript with the HTML template using directives to establish the connection is done

First for the `<form> element` in our HTML, we use `[formGroup] directive` _to associate it with the signupForm in TypeScript_
`<form [formGroup]="signupForm">`
This will tell Angular to use our provided form group, preventing it from creating an auto detected form

Then for each input element like the username, we use the `formControlName directive` _to specify the name of the corresponding control in our TypeScript form_

Like if we have a control named 'username' we use `formControlName="username"` to link it to the input element

- We repeat this process for all form controls we want to connect to their respective HTML input elements

In `app.component.html`:

```
<form [formGroup]="signupForm">

...
 <input
  type="text"
  id="username"
  formControlName="username"
  class="form-control">

...
 <input
  formControlName="email"

...
 <input
  formControlName="gender"
```

This synchronization ensures that the HTML elements work in harmony with the form controls defined in TypeScript, making our form fully functional
