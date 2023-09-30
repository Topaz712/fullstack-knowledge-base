# Adding Content to the Recipes Components

First we add the Recipe Model

Then when we do that we import the Recipe Model in the `recipe-list.component.ts`
Navigate up one folder to access the Recipe model so it'll look like: `import { Recipe } from '../recipe.model';`

Once we've added the Recipe model we define the type for the recipes property as an array of Recipe objects, like so:

```
exort class RecipeListcomponent implements OnInit {
  recipes: Recipe[] = [
    new Recipe('A Test Recipe', 'This is simply a test', 'image link path')
  ];

  constructor() {}

  ngOnInit() {

  }
}
```

Finally we'll do the template setup by creating a placeholder for a single recipe item and style the image in the recipe item.

We would do this with a bootstrap layout with rows and columns, like so:

```
<div class="row">
  <div class="col-xs-12">
    <button class="btn btn-success">New Recipe</button>//Add a "New Recipe" button
  </div>
</div>
<div class="row">
  <div class="col-xs-12">
    <a href="#" class="list-group-item clearfix">
      <div class="pull-left">
        <h4 class="list-group-item-heading">Recipe Name</h4>
        <p class="list-group-item-text">Description</p>
      </div>
      <span class="pull-right">
        <img src="" alt="" class="img-responsive" style="max-height: 50px;">//resize the image appropriately
      </span>
    </a>
    <app-recipe-item></app-recipe-item>
  </div>
</div>
```

So for this we provided a code set up for the recipe-list component, imported the Recipe model, and prepared the template structure for displaying recipes.

- Dynamic data will be added later to replace the placeholder content since we'll need to replicate the item again
