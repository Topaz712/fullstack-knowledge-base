# TD: Creating the Form and Registering the Controls

In this section, we're learning how to create forms and specify their parts, in the template-driven method

In our Angular app, we have to make sure to import the Forms Module in `app.module.ts` , it's a built-in module for handling forms in Angular then we add it to the imports array as well:

```
import { FormsModule } from '@angular/forms';

imports: [
    BrowserModule,
    FormsModule
  ],
```

When Angular detects a form element in our HTML code, it automatically creates a JavaScript object representing the form

Angular won't automatically detect our input elements as controls in the form so we need to tell Angular which inputs should be treated as controls manually

To register an input as a control, we use the ngModel directive, which is part of the Forms Module

We add ngModel to our input element without square brackets or parentheses
in `app.component.html`:

```
<input
  type="text"
  id="username" class="form-control"
  ngModel>
  ...
<input
  type="email"
  id="email"
  class="form-control"
  ngModel>
  ...
<select
  id="secret"
  class="form-control"
  ngModel>
```

To ensure Angular knows the name of each control, we use the standard HTML attribute name

So like if we want to register an input with the name "username" we add it as `name="username"`
like so:

```
<input
  type="text"
  id="username" class="form-control"
  ngModel
  name="name">
  ...
<input
  type="email"
  id="email"
  class="form-control"
  ngModel
  name="email">
  ...
<select
  id="secret"
  class="form-control"
  ngModel
  name="secret">
```

We registered each control in our form by doing the same process for each input element we wanted to include in the form

This sets up our form and the controls inside it, but we'll explore how to interact with and submit the form in the next video lesson
