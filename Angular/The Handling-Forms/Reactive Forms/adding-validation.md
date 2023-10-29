# Reactive: Adding Validation

In this lesson, we're adding validation to our reactive form

**The difference with the template-driven approach, where we added validation directly in the HTML template, is that in the reactive approach, it configures validation in the TypeScript file**

- First we import _Validators from @angular/forms_

  - In the _ngOnInit method_, we initialize our form controls and specify validation rules, like for the username control, we use the `Validators.required` validator, ensuring that the field must not be empty

  - Then for the email control, we apply two validators, `Validators.required and Validators.email` because the first one checks for empty fields and the second one ensures that the input is a valid email address

In `app.component.ts`:

```
import { FormControl, FormGroup, Validators } from '@angular/forms';

...
ngOnInit() {
    this.signupForm = new FormGroup({
      'username': new FormControl(null, Validators.required),
      'email': new FormControl(null, [Validators.required, Validators.email]),
      'gender': new FormControl('female')
    });
  }

```

These validators are provided as references without executing them, _omit the paranthesis so it doesnt execute as a method_ Angular will execute them as needed, based on user input, providing effective validation for our form controls
