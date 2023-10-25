# TD: Grouping Form Controls

In this lesson, Max teaches us how to better organize and control our form elements in the application and how this feature gives us more control, letting us group and manage form elements while ensuring validation and interactivity

We can group related form controls to add structure to our form

- In the `app.component.html` we use the _ngModelGroup directive_ to create a group
  - This directive requires a string key, like _'userData'_ to define the group

in `app.component.html`:

```
<div
  id="user-data"
  ngModelGroup="userData"
  #userData="ngModelGroup">

.......

<p *ngIf="!userData.valid && userData.touched">User Data is invalid!</p>
```

- When we submit the form, the value object we receive will reflect the structure of our groups in the console

  - Like if we have a 'userData' group that contains email and username, the value object will show an object hierarchy that mirrors this structure

- We can apply validation and interact with these groups just like individual form controls
  - We can check the validity and other properties of the group, like _dirty, touched, and valid_, these properties allow us to perform fine grained validation

To access the JavaScript object associated with a group, we create a local reference, similar to how we reference individual form controls, like using `#userData="ngModelGroup"`

We can display messages based on the validity of the group, by checking properties with `*ngif` with like `userData.valid and userData.touched` we can show messages when the user interacts with the group and the data is invalid
