# Why do we Need Angular's Help?

Angular creates a JavaScript object that represents our HTML form

```
<form>
<label>Name</label>
<input tvpe= "text" name="name">
<label>Mail</label>
<input type= "text name-"email">
<button type= "submit"> Save</button>
</form>
```

and

```
{
  value: {
    name: 'Max',
    email: 'test@test.com'
  }
  valid: true
}
```

- This representation includes key-value pairs with keys corresponding to input names and user-entered values
  - This object contains the form's values and information about its state, like whether it's valid
  - This object makes it easier to work with form data in your TypeScript code
  * In the upcoming lectures, we'll learn how Angular configures and handles this object, allowing us to work effectively with forms
