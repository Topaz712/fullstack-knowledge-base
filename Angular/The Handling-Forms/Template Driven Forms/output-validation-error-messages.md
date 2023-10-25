# TD: Outputting Validation Error Messages

We add validation error messages to enhance the user experience

So below an input, we use a Bootstrap class called `help-block` for styling

_We create a local reference_ for the input element, like `#email` and _associate it with ngModel_

```
<input
  type="email"
  id="email"
  class="form-control"
  ngModel
  name="email"
  required
  email
  #email="ngModel">
<span class="help-block" *ngIf="!email.valid && email.touched">Please enter a valid email!</span>
</div>
```

This will display the help text only if email is not valid and has been touched, ensuring that the warnings appear when needed and disappear when the input is valid

This way, we can provide the right feedback and styling based on the form's state
