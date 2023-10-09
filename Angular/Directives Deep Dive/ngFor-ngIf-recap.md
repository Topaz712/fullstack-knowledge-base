# ngFor and ngIf Recap

## ngIf

- For this recap we learned that `*ngIf` is commonly used for showing or hiding elements like error messages, login/logout buttons, or sections of a page based on user permissions or application states
  - We use \*ngIf with a condition that evaluates to either true or false
  - Elements enclosed in an `*ngIf` block are displayed only when the condition is true, and they are removed from the DOM when the condition is false

## ngFor

- `*ngFor` is a structural directive used to iterate over a collection like an array or list of sorts and generate HTML elements for each item in the collection
  - It allows us to dynamically render multiple elements in our template based on the data provided
    Like so : `*ngFor="let item of items"` iterates through the items array and assigns each item to the item variable

## Combined

- We see that it's pretty common to use `*ngFor` along with `*ngIf` to conditionally render elements within a loop
  - Like we might use `*ngFor` to iterate over items and use `*ngIf` to filter and display specific items based on a condition

Like in these videos where we want to iterate an array of numbers only if they are even or odd
