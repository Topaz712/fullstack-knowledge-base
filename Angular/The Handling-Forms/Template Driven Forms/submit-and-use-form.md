# TD: Submitting and Using the Form

In this video, we're setting up a form and making it submittable using the template-driven approach

In `app.component.html` we create the form with an _(ngSubmit) event binding_ and this event will trigger when the form is submitted

- Then to trigger the onSubmit method when the form is submitted, we attached _(ngSubmit) to the form element_, and defined the method name
  - Then we added a local reference, like `#f` to the form element to access it in the template
  - After this, we passed the reference as an argument to the onSubmit method
  * To access the JavaScript object representing the form automatically created by Angular, we set the local reference equal to _ngForm_
  * Now, the onSubmit method can log the form object, and we can see the values entered by the user

So in `app.component.html`:

```
<form
  (ngSubmit)="onSubmit(f)"
  #f="ngForm" >
```

So in our _app.component.ts_ we import _NgForm from @angular/forms_ and create an _onSubmit() method_ that takes the form as an argument

in `app.component.ts`:

```
import { NgForm } from '@angular/forms';

  onSubmit(form: NgForm) {
    console.log(form)
  }
```

When we expand the form object in the console, we find key-value pairs where the names of the controls like "username" and "email" match the values the user entered

So by following these steps, we set up a submittable form and accessed the form object created by Angular in the template-driven approach
