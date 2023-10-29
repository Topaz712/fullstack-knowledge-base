# Reactive: Reacting to Status or Value Changes

- `valueChanges` - This observable allows us to monitor changes in the form values

  - When we subscribe to it, we can react to value changes in console, which are fired whenever a form value is altered in app

- `statusChanges` - This observable helps us track the status of the form, which can be 'VALID', 'INVALID', or 'PENDING'
  - By subscribing to it, we can react to changes in the overall form's validation status

In _app.component.ts_:

```
  ngOnInit() {
    this.signupForm = new FormGroup({
      'userData': new FormGroup({
        'username': new FormControl(null, [Validators.required, this.forbiddenNames.bind(this)]),
        'email': new FormControl(null, [Validators.required, Validators.email], this.forbiddenEmails)
      }),
      'gender': new FormControl('female'),
      'hobbies': new FormArray([])
    });
    // this.signupForm.valueChanges.subscribe(
    //   (value) => console.log(value)
    // );
    this.signupForm.statusChanges.subscribe(
        (status) => console.log(status)
      );
  }
```

We can use these observables at the form level or on individual form controls to closely monitor changes in values or validation statuses

Subscribing to these observables helps us learn about the form's behavior, enabling us to create interactive features and offer user feedback based on their interactions with the form
