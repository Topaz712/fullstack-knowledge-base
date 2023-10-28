# TD: Setting and Patching Form Values

To set up our form values, we will create a function to set form values programmatically using _setValue()_ in `app.component.ts`:

```
  suggestUserName() {
    const suggestedName = 'Superuser';
    // this.signupForm.setValue({
    //   userData: {
    //     username: suggestedName,
    //     email: ''
    //   },
    //   secret: 'pet',
    //   questionAnswer: '',
    //   gender: 'male'
    // });
    this.signupForm.form.patchValue({
      userData: {
        username: suggestedName
      }
    });
  }
```

- With _suggestUserName()_ function it sets values for the entire form using `setValue()`
- It overwrites all fields with predefined values
- However, this approach might not be suitable when we want to keep existing values

- Alternatively, _a better approach is to use patchValue() on the form object_ itself because it's more suitable for preserving existing values while updating only the necessary ones
  - To access the form object we use `this.signupForm.form.patchValue()` because it allows us to selectively override specific form controls without affecting others

In `app.component.ts`:

```
<button
  class="btn btn-default"
  type="button"
  (click)="suggestUserName()">
  Suggest an Username
</button>
```

We add a button element to trigger the action

So basically, we can use **setValue() to set values for the entire form or patchValue() to selectively update specific form controls**, either way, both methods provide flexibility in managing form data programmatically
