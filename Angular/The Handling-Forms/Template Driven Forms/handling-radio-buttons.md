# TD: Handling Radio Buttons

The genders array is defined with the available options, in this case, 'male' and 'female' although to not offend anyone, it's acknowledged there are more genders, for this lesson we stick to simple though

- This setup will let us create a group of radio buttons in our form, where users can select one of the predefined gender options and the form ensures that a choice is made before submission

In `app.component.ts`:

`genders = ['male', 'female'];`

And

In `app.component.html`:

```
<div class="radio" *ngFor="let gender of genders">
  <label>
    <input
      type="radio"
      name="gender"
      ngModel
      [value]="gender"
      required>
    {{ gender }}
  </label>
</div>
```

- Radio buttons are set up using an `*ngFor` loop to iterate through the `genders` array

- Each radio button is contained within a div with the _Bootstrap class "radio"_ and is associated with the ngModel directive for two-way data binding
  - It is wrapped in a label for styling and accessibility
  - The input is set to type "radio" to create a radio button
  - The name attribute is set to "gender" to group the radio buttons
  - The `[value]` attribute binds the value to the corresponding gender
  - The `required` attribute ensures that a selection is mandatory
  - Then use interpolation `{{ gender }}` to display the gender options
