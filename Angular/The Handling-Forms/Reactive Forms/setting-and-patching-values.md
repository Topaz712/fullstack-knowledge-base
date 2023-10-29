# Reactive: Setting and Patching Values

## setValue

- We use `this.signupForm.setValue({ })` to populate the entire form with predefined values
  - This provides an object that matches the form's structure to set values for all the fields

## patchValue

- We use `this.signupForm.patchValue({ })` to update specific parts of the form, leaving the rest untouched
  - This is ideal for making partial updates without affecting the whole form

In _app.component.ts_:

```
    this.signupForm.setValue({
      'userData': {
        'username': 'Topaz',
        'email': 'topaz@test.com'
      },
      'gender': 'female',
      'hobbies': []
    });
    this.signupForm.patchValue({
      'userData': {
        'username': 'Max',
      }
    });
}

  onSubmit() {
    console.log(this.signupForm);
    this.signupForm.reset();
  }
```

In onSubmit() the form data is logged to the console and we reset the form with `this.signupForm.reset()` to clear it for new input

By using these methods, we can easily control and change form data according to our application's requirements
