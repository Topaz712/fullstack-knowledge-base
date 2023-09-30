# Using the Components

Then to see it displayed on our browser we add the 'app-recipes' selector in our `app.component.html` "the main HTML page" and so far our page looks like this:

```
<app-header></app-header>
<div class="container">
  <div class="row">
    <div class="col-md-12">
      <app-recipes></app-recipes>
    </div>
  </div>
</div>
```

In our app we want the components to be displayed next to each other so in our `recipes.component.html` we would set it up like this with bootstrap:

```
<div class="row">
  <div class="col-md-5">
    <app-recipe-list></app-recipe-list>
  </div>
  <div class="col-md-7">
      <app-recipe-detail></app-recipe-detail>
  </div>
</div>
```

For our shopping-list component we now roughly set up what we want to have in it, which is our shopping-edit component so:

```
<div class="row">
  <div class="col-xs-10">
    <app-shopping-edit></app-shopping-edit>
  <hr>
  <p>The list</p>
  </div>
</div>
```
