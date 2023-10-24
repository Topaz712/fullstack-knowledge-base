# TD: Accessing the Form with @ViewChild

- We can submit a form by passing the form we get through _ngForm_ to the _onSubmit_ method

  - This is a common approach

- An alternative method to access the form is using the _@ViewChild decorator_ which we learned about earlier

  - We do this by importing it from _'@angular/core'_

- To use _@ViewChild_ we specify the local reference like 'f' as a string argument and store it in a variable, like _signUpForm_ and the variable will be of type _ngForm_
  ` @ViewChild('f') signupForm: NgForm;`

- Using _@ViewChild_ provides access to the form without explicitly passing it to the _onSubmit()_ of the html file

- This approach is helpful if we need to access the form earlier, and not just when we are submitting it
