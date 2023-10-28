# TD: Using Form Data

In `app.component.ts` we create a user object with properties for username, email, secret question, answer, and gender, then Initialize them with empty strings

- Under this, we add a `submitted` property and set it to false

In `app.component.ts`:

```
user = {
    username: '',
    email: '',
    secretQuestion: '',
    answer: '',
    gender: ''
  };
  submitted = false;

............

onSubmit() {
    this.submitted = true;
    this.user.username = this.signupForm.value.userData.username;
    this.user.email = this.signupForm.value.userData.email;
    this.user.secretQuestion = this.signupForm.value.userData.secret;
    this.user.answer = this.signupForm.value.userData.questionAnswer;
    this.user.gender = this.signupForm.value.gender;
  }
}

```

Now when the form is submitted, we make sure to set the submitted property to true

Then to update the properties of the user object with the corresponding values from the form we use `this.signupForm.value.`

In this case, `userData` is added first because it's the container for the user related data fields so after this we can access the values of the individual/specific form fields we want, it was our way of grouping related form controls together in our html file, in the form element, like so:

```
<form
  (ngSubmit)="onSubmit()"
  #f="ngForm">
  <div
    id="user-data" ngModelGroup="userData"
    #userData="ngModelGroup">
    <div class="form-group">
      <label for="username">Username</label>
```

So because of this `ngModelGroup` directive in our html we used to group the related form controls under the `"userData"` container , we access the specific form fields after it, with dot notation

In `app.component.html`:

```
</div>
  <hr>
  <div class="row" *ngIf="submitted">
    <div class="col-xs-12">
      <h3>Your Data</h3>
      <p>Username: {{ user.username }}</p>
      <p>Mail: {{ user.email }}</p>
      <p>Secret Question: Your first {{ user.secretQuestion }}</p>
      <p>Answer: {{ user.answer }}</p>
      <p>Gender: {{ user.gender }}</p>
    </div>
```

We used conditional rendering to display the user data only if the form has been submitted with `*ngIf` to output the user's username, email, secret question, answer, and gender
