# Creating an "Ingredient" Model

- Creating an "Ingredient" Model makes sense because we'll be using ingredints alot in the application

We created a shared folder in the app folder
In the share folder we created a file called `ingredient.model.ts` so that we could export the class Ingredient model

a typical setup looks like:

```
export class Ingredient {
  public name: string;
  public amount: number;

  constructor(name: string, amount: number) {
    this.name = name;
    this.amount = amount;
  }
}
```

but a shortcut way to do this is that will gives us the same effect:

```
export class Ingredient {
  constructor(public name: string, public amount: number) {}
}
```

So with this, we defined how ingredient is suppose to look.
