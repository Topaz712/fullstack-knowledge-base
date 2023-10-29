# Reactive: Using Error Codes

Angular associates error codes with form controls when validation fails, so we can access these error codes using `signupForm.get('controlName').errors` in _app.component.html_  
We can create conditional error messages based on these error codes using `*ngIf` and it will let us display custom error messages to users

In _app.component.html_:

```
<span
  *ngIf="!signupForm.get('userData.username').valid && signupForm.get('userData.username').touched" class="help-block">
  <span *ngIf="signupForm.get('userData.username').errors['nameIsForbidden']">This name is invalid!</span>
  <span *ngIf="signupForm.get('userData.username').errors['required']">This field is required!</span>
</span>
```

We can check for specific error codes like 'nameIsForbidden' and 'required' and display corresponding messages
With this, we can use error codes to give users specific error messages related to their input
