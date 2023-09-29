# Creating Components with the CLI & Nesting Components

We can use the vscode terminal to generate a new component like so: `ng generate component pickaName` or use the shorthand with `ng g c pickaName`

This will _gives us a new folder_ in our app folder with the name of our component and it _will have all the necessary files inside_

After this we need to make sure to update our `app.module.ts` and even though the CLI should automatically import and declare the component we should still check.

So by nesting components we are _putting the components selector_ which we created _inside of another component_, so now it **makes the first component a part of the second one and so on.**
