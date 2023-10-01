# Working on the ShoppingListComponent

For this part of the video we worked on adding an ingredients property to the `shopping-list.component.ts` so we could display it in our `shopping-list.component.html`

For `shopping-list.component.ts` in the class , above the constructor we added : `ingredients = [];`

_Like with the recipe, we will end up using ingredients alot so creating a model for ingredients is the way we will go about it._

`shopping-list.component.html` :

```
<div class="row">
  <div class="col-xs-10">
    <app-shopping-edit></app-shopping-edit>
    <hr>
    <ul class="list-group">
      <a class="list-group-item" style="cursor: pointer"></a>
    </ul>
  </div>
</div>
```
