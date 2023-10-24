# TD: Adding Validation to check User Input

- Validation of user input is essential for any app

- When using the template-driven approach, validation is added within the template

- Angular provides built-in directives to add validation to form elements

- `required` is a default HTML attribute that can be used for validation
  In `app.component.html`:

```
<input
  type="text"
  id="username" class="form-control"
  ngModel
  name="username"
  required>

<input
  type="email"
  id="email"
  class="form-control"
  ngModel
  name="email"
  required
  email>
```

- `email` is an Angular directive to ensure a valid email address

- When validation rules are applied, the form's 'valid' attribute indicates if the form is valid overall

- Angular dynamically adds classes like `ng-dirty` `ng-touched` and `ng-valid` to help style the inputs conditionally
  - Angular tracks the state of controls individually and gives us information about whether they are "dirty", "touched", and whether it is "valid" or not

These classes provide information about the control's state and can be used to enhance the user experience
