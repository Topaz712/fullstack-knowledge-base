# Displaying Recipe Details

In the `recipe-detail.component.html` , we will have all the logic inside of it which we need to display the details and then having some options to go to another place in our app or have it be trigger something else as well like editing the recipe but that's something we'll learn to do later in the course.

```
<div class="row">
  <div class="col-xs-12">
    <img scr="" alt="" class="img-responsive">
  </div>
</div>
<div class="row">
  <div class="col-xs-12">
    <h1>Recipe Name</h1>
  </div>
</div>
<div class="row">
  <div class="col-xs-12">
    <div class="btn-group">
      <button
        type="button"
        class="btn btn-primary dropdown-toggle">
        Manage Recipe <span class="care"></span>
      </button>
      <ul class="dropdown-menu">
        <li><a href="#">To Shopping List</a></li>
        <li><a href="#">Edit Recipe</a></li>
        <li><a href="#">Delete Recipe</a></li>
      </ul>
    </div>
  </div>
</div>
<div class="row">
  <div class="col-xs-12">
    Ingredients
  </div>
</div>
```
