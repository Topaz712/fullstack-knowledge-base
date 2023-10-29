# Reactive: Grouping Controls

In this lesson, we will learn how to group controls in a reactive form and access nested form controls in the HTML template so we can easily handle nested controls and ensure that they are correctly synchronized in our reactive forms

In _app.component.ts_, we can create a FormGroup with nested controls like so:

```
ngOnInit() {
    this.signupForm = new FormGroup({
      'userData': new FormGroup({
        'username': new FormControl(null, Validators.required),
        'email': new FormControl(null, [Validators.required, Validators.email])
      }),
      'gender': new FormControl('female')
    });
  }
```

Then in _app.component.html_, when we work with nested controls, we use the formGroup and formControlName directives to maintain the structure, like when nesting controls under 'userData':

```
<div formControlName="userData">
  <div class="form-group">
    <label for="username">Username</label>
    <input
      type="text"
      id="username"
      formControlName="username"
      class="form-control">
    <span
      *ngIf="!signupForm.get('userData.username').valid && signupForm.get('userData.username').touched" class="help-block">Please enter a valid username!</span>
  </div>
  <div class="form-group">
    <label for="email">email</label>
    <input
      type="text"
      id="email"
      formControlName="email"
      class="form-control">
    <span
      *ngIf="!signupForm.get('userData.email').valid && signupForm.get('userData.email').touched" class="help-block">Please enter a valid email!</span>
  </div>
```

If we have nested form controls, we should remember to provide the path to the control using dots when using `signupForm.get()` like, `signupForm.get('userData.username')` _to access the 'username' control nested under 'userData'_

So by grouping controls in nested form groups it allows for a more organized structure, especially when dealing with complex forms with multiple levels of nesting
