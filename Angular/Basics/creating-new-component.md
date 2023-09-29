# Creating a New Component

It's good practice to have our folder name be the same as our component name and each component should typically have its own folder.

- A good naming convention is to have the name of the component first, then dot, then component,then dot and whatever file we want it to be.

  > For example `server.component.ts`

- A Component is a simply a TypeScript class, so that Angular is able to instantiate it to creat the objects based on the blueprint we set up.
  > then we would need to export the class

in the `server.component.ts` we would do

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-server',
  templateUrl: './server.component.html'
})
export class ServerComponent {

}
```

- Adding `@Component` to the class is a decorator and it lets Angular know its 'special'

  > **Decorators are a TypeScript feature which allows us to enhace our classes**

- Then we have to add an import to give us acces to components by doing `import { Component } from '@angular/core';`

- Then we add a selector property/properties like `'app-server'` which will let us use our component in our other components

  > usually it should say `app` first and then the name of our component

- Then we create the `server.component.html` file that will hold the template "the html code of our component"

Now that we have done that, we need to put `templateUrl: './server.component.html'` in our `server.component.ts` file to give it a relative path to our server html file
