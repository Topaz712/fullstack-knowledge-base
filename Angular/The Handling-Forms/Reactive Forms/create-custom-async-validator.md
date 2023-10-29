# Reactive: Creating a Custom Async Validator

We define the _forbiddenEmails method_ and have it take control as an argument and return either a Promise or an Observable to handle asynchronous validation

In the _forbiddenEmails method_ we create a Promise with a delay using setTimeout to check if the control value matches a forbidden email address like'test@test.com' and if it matches, resolve the Promise with an object containing an error code `('emailIsForbidden')`, if it doesn't match, resolve with null and at the end we do return promise

```
import { FormArray, FormBuilder, FormControl, FormGroup, Validators } from '@angular/forms';
import { Observable } from 'rxjs/Observable';

forbiddenEmails(control: FormControl): Promise<any> | Observable<any> {
    const promise = new Promise<any>((resolve, reject) => {
      setTimeout(() => {
        if (control.value === 'test@test.com') {
          resolve({'emailIsForbidden': true});
        } else {
          resolve(null);
        }
      }, 1500);
    });
    return promise;
  }
```

In _app.component.ts_ where we set up our email form control, that includes built in validators like 'required' and 'email', is where we add our custom asynchronous validator, `this.forbiddenEmails` like so:

`'email': new FormControl(null, [Validators.required, Validators.email], this.forbiddenEmails)`

We add the custom asynchronous validator to the email form control by passing it as the third argument when setting up the FormControl

- Now when users input an email, the asynchronous validator will check it after a delay, and the field's validation status will update accordingly

So by havaing this custom asynchronous validator we can simulate asynchronous operations like checking email uniqueness by waiting for a response
