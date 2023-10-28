# TD: Resetting Forms

In the last lecture, we learned how to submit a form and extract the data but if we want to reset the form we add it at the end of the `onSubmit()` function as `this.signupForm.reset();`

- We call the _reset() method_ on signupForm, so it resets the form entirely
  - This means it clears all the form inputs and resets properties like validity and touched states which is a handy way to refresh the form as if the page was loaded again

In `app.component.ts`:

```
onSubmit() {
  this.submitted = true;
  this.user.username = this.signupForm.value.userData.username;
  this.user.email = this.signupForm.value.userData.email;
  this.user.secretQuestion = this.signupForm.value.userData.secret;
  this.user.answer = this.signupForm.value.userData.questionAnswer;
  this.user.gender = this.signupForm.value.gender;

  this.signupForm.reset();
}
```
