# Creating and Outputting the Shopping List

Now that we've created the ingredient model, just like with recipe we can now define the type for ingredients array as long as we import ingredient to the `shopping-list.component.ts` so that would look like :
`import { Ingredient } from '../shared/ingredient.model';`

so now in that same file for the ShoppingListComponent class we can create our new ingredients :

```
export class ShoppingListComponent implements OnInit {
  ingredients: Ingredients[] = [
    new Ingredient('Apples', 5),
    new Ingredient('Tomatoes', 10),
  ]

  constructor() {}

  ngOnInt() {

  }
}
```

After doing this, we output it to the `shopping-list.component.html`
using a `*ngFor` in the anchor tag `<a>` to loop through all our ingredients and then we output the ingredient data inside the anchor tag `<a>` :

_the parenthesis for ingredient.amount is not angular syntax, it's just regular text so the end result will look like this on the page --> Apples (5) Tomatoes (10) <-- tomatoes is under apples though becuase it is a row after all_

```
<div class="row">
  <div class="col-xs-10">
    <app-shopping-edit></app-shopping-edit>
    <hr>
    <ul class="list-group">
      <a
      class="list-group-item"
      style="cursor: pointer"
      *ngFor="let ingredient of ingredients"
      > {{ ingredient.name }} ({{ ingredient.amount }})</a>
    </ul>
  </div>
</div>
```
