# Outputting a List of Recipes with ngFor

We'll use string interpolation in the `h4` since it allows us to output some text anywhere in our template.

- `ngFor` is a directive that allows us to repeat code in our template
  > So we will use this to loop through our recipes

```
<div class="row">
  <div class="col-xs-12">
    <button class="btn btn-success">New Recipe</button>
  </div>
</div>
<hr>
<div class="row">
  <div class="col-xs-12">
    <a
    href="#"
    class="list-group-item clearfix"
    *ngFor="let recipe of recipes">
      <div class="pull-left">
        <h4 class="list-group-item-heading">{{ recipe.name }}</h4>
        <p class="list-group-item-text">{{ recipe.description }}</p>
      </div>
      <span class="pull-right">
        <img
        src="{{ recipe.imagePath }}"
        alt="{{ recipe.name }}"
        class="img-responsive"
        style="max-height: 50px;">
      </span>
    </a>
    <app-recipe-item></app-recipe-item>
  </div>
</div>
```

By adding string interpolation for the `h4`, we've got a single recipe but it's going to be an object looking like our model, because our recipes array simply holds an array of our recipes

We're just using the recipe properties names we set up in the model.

For the imagePath we can either do `src="{{ recipe.imagePath }}"` or `[src]= "recipe.imagePath"` we can either do string interpolation or property binding but never both for the same one

- It's important To note that we should use the names above the constructor because the ones in the constructor are not available outside of the model
  so the simple item will look like in our `recipe.model.ts`:

```
Export class Recipe {
  public name: string;
  public description: string;
  public imagePath: string;

  constructor(name: string, desc: string, imagePath: string){
  this.name = name;
  this.description = desc;
  this.imagePath = imagePath;
  }
}
```
