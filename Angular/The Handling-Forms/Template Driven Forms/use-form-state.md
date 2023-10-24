# TD: Using the Form State

We can utilize form state for better interactions and visual cues in our Angular application

- In this lesson we will disable the submit button when the form is invalid using property binding
  - We set [disabled] to _!f.valid_ where `f` is the local reference of the form

In `app.component.html`:

```
<button
class="btn btn-primary"
type="submit"
[disabled]="!f.valid">Submit</button>
```

Now we apply CSS styles to the invalid controls by targeting _input.ng-invalid.ng-touched_ in our stylesheet and we give it a visual red border to the invalid inputs _but only if they've been touched_

In `app.component.css`:

```
input.ng-invalid.ng-touched {
border: 1px solid red;
}
```

We also provide feedback messages to users by adding a message below an input field and conditionally showing it with `*ngIf`
We want to show `"Please enter a valid value!"` based on the control's value

In `app.component.html`:

```
<div class="form-group">
  <label for="email">Mail</label>
  <input
    type="email"
    id="email"
    class="form-control"
    ngModel
    name="email"
    required
    email>
</div>
<p *ngIf="">Please enter a valid value!</p>
</div>
```

**So basically, by using Angular's built-in tools and form state, we can make our app more user friendly like showing users which parts of a form are incorrect/incomplete and giving them helpful messages**
