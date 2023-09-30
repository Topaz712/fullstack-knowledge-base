# Creating a "Recipe" Model

## What is a model?

- It is simply a TypeScipt file

Since we'll be _using recipe alot_ in the app, we are going to _clearly define it_ so whenever we use it in any component, _it will always be talking about the same structure, the same kind of object_.

- **The Model in the end is just a blueprint for objects we create and the TypeScript class does this job.**

  > that is why we would need a model `recipe.mode.ts` in the recipes folder

- In the `recipe-list.component.ts` we add an array of `recipes[];` for the `RecipeListComponent` class and then in the `recipe.model.ts` we do:

```
export class Recipe {
  public name: string;
  public description: string;
  public imagePath: string; //to hold images/can be from the web

  constructor(name: string, desc: string, imagePath: string) {
    this.name = name;
    this.description = desc;
    this.imagePath = imagePath;
  }
}
```
