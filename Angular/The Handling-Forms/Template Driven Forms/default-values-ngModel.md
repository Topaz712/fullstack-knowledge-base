# TD: Set Default Values with ngModel Property Binding

To set default values using ngModel with property binding, in `app.component.html` we use _square brackets []_ for property binding and _bind ngModel_ to a default value or property

In `app.component.html`:

```
<select
  id="secret"
  class="form-control"
  [ngModel]="defaultQuestion"
  name="secret">
  <option value="pet">Your first Pet?</option>
  <option value="teacher">Your first teacher?</option>
</select>
```

Then in `app.component.ts` we define the _defaultQuestion property_ with the desired default value

In `app.component.ts`:

`defaultQuestion = 'teacher';`

This approach allows us to set default values for form elements, like dropdowns and inputs, which lets users still change, if needed

We should also keep in mind that we can set default values without using ngModel, we can use one-way binding 'property binding' to define a default value for our form elements
