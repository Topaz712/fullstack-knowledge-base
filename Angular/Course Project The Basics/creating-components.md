# Creating the Components

Not every components should have a folder on the root level, we should also nest them by feature

In this video Max suggests for us to create them in the CLI as well as manually

First we created the header folder directly in the app root folder since it is mainly only used by the app component

Next we created the `header.component.ts` file in the header folder

- Since a component is simply a TypeScript class, we name it `HeaderComponent` but it wont be recognized by Angular as a component unless we add the `@Component` decorator above it
  - After this we import it manually from `@angular/core`
- Once we've dont that we need to pass a JavaScript object to the decorator to configure that component in `@Compontent({ })`
  - In here usually we add a `selector:` so we could use this component like `app-header` a unique selector, as to not overwrite existing HTML elements or so, then `templateUrl:` for external file or also `template:` is also fine
  * In the `templateUrl` we point to the `header.component.html` file we have also created in the header folder

so it should look like this all together:

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-header',
  templateUrl: './header.component.html';
})
export class HeaderComponent {

}
```

**It's very important to remember to register all our features we're going to use in the `app-module.ts` file**

- We import header component and point to the header folder `import { HeaderComponent } from './header.component';` then add `HeaderComponent` in the declarations array right under the `AppComponent` in that list

We can then add insert this selector `<app-header></app-header>` into the `app.component.html`, but probably best to place it above our div container since we only want the container to contain our content component
So it would look like this:

```
<app-header></app-header>
<div class="container">
  <div class="row">
    <div class="col-md-12">
      <h2>I'm working!</h2>
    </div>
  </div>
</div>
```

## Generating a Component with the CLI

When we create a component with CLI in the terminal `ng g c recipes` "the shorthand version" for our overall recipes components to be contained in and it will create its own folder with all the files we would usually need and it also automatically imports its components in the `app.module.ts` but we should always check just in case

Then when we want to embed another component's folder in that first folder, we would create it as a subfolder `ng g c recipes/recipe-list`
so it's looks like:

- recipes

  - recipe-list
    - recipe-item
  - recipe-detail

- shopping list
  - shopping-edit

That is how we structure our folders by feature
