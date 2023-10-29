# Reactive: Submitting the Form

In our `app.component.ts` we create an _onSubmit method_:

```
onSubmit() {
  console.log(this.signupForm);
}
```

With the reactive approach, we don't need to grab the form element separately like in the template driven approach, we can just _log the signupForm directly_ since we created the form in TypeScript

Now in the `app.component.html` we use the _(ngSubmit) directive_ to react to the form's submit event, just like in the template-driven approach:

`<form [formGroup]="signupForm" (ngSubmit)="onSubmit()">`

So by logging `this.signupForm in the onSubmit method in our Typescript`, we can access and view the form's values, which are represented as an object

The reactive approach allows for a more structured and clearer mapping connection of the form data to our app's model in console
