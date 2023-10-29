# Reactive: Getting Access to Controls

In this lesson, we learn how to access and display validation messages

In _app.component.css_ we define styling for invalid and touched inputs:

```
input.ng-invalid.ng-touched {
  border: 1px solid red;
}
```

Now in the HTML template of our _app.component.html_, we add validation messages for form controls, to display a message below the username and email inputs

- We use the _ngIf directive to conditionally display messages_ based on control validity and touch status
  - To access a control in our form, we use the `signupForm.get('username') method`, and 'username' is the name of the control we want to access
    - We check if a control is valid and if it has been touched using the `.valid and .touched` properties

In _app.component.html_:

```
<input>
<span
  *ngIf="!signupForm.get('username').valid && signupForm.get('username').touched" class="help-block">Please enter a valid username!</span>
</div>

...
<input>
<span
  *ngIf="!signupForm.get('email').valid && signupForm.get('email').touched" class="help-block">Please enter a valid email!</span>
</div>

...
</div>
<span
  *ngIf="!signupForm.valid && signupForm.touched" class="help-block">Please enter valid data!</span>
<button class="btn btn-primary" type="submit">Submit</button>
</form>
```

This approach lets us display validation messages based on control status, providing a clear way to guide users when they enter incorrect data
