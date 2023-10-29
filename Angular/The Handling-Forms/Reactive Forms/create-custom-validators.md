# Reactive: Creating Custom Validators

To create custom validators in Angular when using the reactive form approach we first define an array of forbidden usernames in our _app.component.ts_ like _forbiddenUsernames_

Then we create a custom validator function like **forbiddenNames** which takes a form control as an argument and returns an object with an error code as a key and a boolean value

If the control value is invalid, we set the error code to true otherwise, have it return null

Then we apply the custom validator to a form control by adding a reference to it in the array of validators for 'username' and make sure not to execute the function but only pass a reference, and we also `bind(this)` to it

In _app.component.ts_:

```
forbiddenUsernames = ['Chris', 'Ana'];

ngOnInit() {
  this.signupForm = new FormGroup({
    'userData': new FormGroup({
      'username': new FormControl(null, [Validators.required, this.forbiddenNames.bind(this)]),

....
forbiddenNames(control: FormControl): {[s: string]: boolean} {
  if (this.forbiddenUsernames.indexOf(control.value)) {
    return { 'nameIsForbidden': true};
  }
  return null;
}
```

This validator checks if the username entered is in the list of forbidden usernames and returns an error code if it matches
