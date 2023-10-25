# TD: Using ngModel with Two-Way-Binding

In this video lesson on using ngModel with two-way binding, we learn how to react instantly to changes in user input

- Sometimes, we want to react immediately to user input changes rather than waiting for form submission because in standard Angular forms, updates occur after form submissions

- To get instant reactions, we can use two-way binding with ngModel
  - This allows us to both input data and display it in real time

Max demonstrates this with a _<textarea> element_ that instantly updates a property called answer

in `app.component.ts`:
`answer = '';`

Then

in `app.component.html`:

```
 <div class="form-group">
  <textarea
    name="questionAnswer"
    rows="3"
    class="form-control"
    [(ngModel)]="answer">
  </textarea>
</div>
<p>Your reply: {{ answer }}</p>
```

We used `[(ngModel)]="answer"` to bind the `textarea` to the _answer property_ and any changes in the textarea are immediately reflected in the answer property

To make sure we can display the user's input using interpolation we did `<p>Your reply: {{ answer }}</p>` under it

But it's important to note that even with two-way binding, we can still capture a snapshot of the value at the point of form submission
