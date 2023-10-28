# Reactive: Creating a Form in Code

In `app.component.ts` we import essential modules including _Component and OnInit_ from '@angular/core' and also import _FormControl and FormGroup_ from '@angular/forms' :

```
import { Component, OnInit } from '@angular/core';
import { FormControl, FormGroup } from '@angular/forms';
```

We declare class properties for genders with an array to hold gender options and signupForm as FormGroup

- To use the ngOnInit lifecycle hook, we Implement the OnInit interface
  - This will ensure that form initialization occurs before rendering the template

Now we create the form in the ngOnInit method, by initializing the signupForm inside the method

- We Create a new FormGroup by passing a JavaScript object with key-value pairs

  - Each key represents a control name like 'username', 'email', and 'gender', each value is a new FormControl

- Now we provide an initial value for each control
  - Like for 'username' and 'email' they're set to a default value of null, while _for 'gender' we're creating a form control and even though it may look like a radio button, Angular treats it as a regular input so we could set it to null, but we choose to set a default gender value_ for it as 'female'

```
export class AppComponent implements OnInit {
  genders = ['male', 'female'];
  signupForm: FormGroup;

  ngOnInit() {
    this.signupForm = new FormGroup({
      'username': new FormControl(null),
      'email': new FormControl(null),
      'gender': new FormControl('female')
    });
  }
}
```
