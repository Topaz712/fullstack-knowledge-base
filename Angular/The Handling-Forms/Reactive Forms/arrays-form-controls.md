# Reactive: Arrays of Form Controls (FormArray)

To allow users to add dynamic form controls, like hobbies, we create a Form Array in our FormGroup in _app.component.ts_ and we initialize the Form Array with an empty array and we can add validation rules if needed

We implement a method `onAddHobby()`, in your component file that creates a new Form Control and pushes it into the Form Array:

```
    }),
      'gender': new FormControl('female'),
      'hobbies': new FormArray([])
    });
  }
....

onAddHobby() {
    const control = new FormControl(null, Validators.required);
    (<FormArray>this.signupForm.get('hobbies')).push(control);
  }

  getControls() {
    return (<FormArray>this.signupForm.get('hobbies')).controls;
  }

  // get controls() {
  //   return (this.signupForm.get('hobbies') as FormArray).controls;
  // } alternatively we can set up a getter and use this alternate type casting syntax and then in the html template do *ngFor="let hobbyControl of controls; let i = index"
```

- Now in _app.component.html_, we create a button that users can click to add new form controls
  - We use `formArrayName` on a wrapping div element to indicate where the Form Array is
  - Use `*ngFor` to loop through the Form Controls within the Form Array and extract their index
  - Then we bind the _formControlName property for each input field_ to link it to the corresponding Form Control using the index

```
<div formArrayName="hobbies">
  <h4>Your Hobbies</h4>
  <button
    class="btn btn-default"
    type="button"
    (click)="onAddHobby()">Add Hobby</button>
    <div
      class="form-group"
      *ngFor="let hobbyControl of getControls(); let i = index">
      <input type="text" class="form-control" [formControlName]="i">
    </div>
</div>
```

Now users can enter values for each dynamically created Form Control and when the form is submitted, the _Form Array_ holds the values entered by the user in the console, which can be used for further processing

Angular handles the validation and error classes like 'valid' or 'touched' automatically based on the validation rules set in the Form Controls

With this approach, we can easily create dynamic forms and collect data from users based on their interactions

_Form Arrays provide a flexible and powerful way to handle such dynamic form elements in Angular applications_
