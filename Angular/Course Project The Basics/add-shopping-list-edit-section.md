# Adding a Shopping List Edit Section

The last thing we are adding to this is the shopping-list-edit section which will display an input field to let us edit or add new items

In the `shopping-edit.html` we'll set it up like:

```
<div class="row">
  <div class="col-xs-12">
    <form>
      <div class="row">
        <div class="col-sm-5 form-group">
          <label for="name">Name</label>
          <input type="text" id="name" class="form-control">
        </div>
        <div class="col-sm-2 form-group">
          <label for="amount">Amount</label>
          <input type="number" id="amount" class="form-control">
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12">
          <button class="btn btn-success" type="submit">Add</button>
          <button class="btn btn-danger" type="button">Delete</button>
          <button class="btn btn-primary" type="button">Clear</button>
        </div>
      </div>
    </form>
  </div>
</div>
```

On our web page it will then have an input field for name and amount, the buttons are right below it , for now it wont do anything but later we will fill it with data so we can manage the ingredient.
