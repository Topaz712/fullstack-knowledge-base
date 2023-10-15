# Setting up and Loading Routes

_Setting up routes helps organize an Angular application and allows users to navigate between different views or components_

To set up routes, we created a const named AppRoutes that holds an array of route configurations in the `app.module.ts`, like so:

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent },
  { path: 'servers', component: ServersComponent },
];
```

Each route configuration consists of a path and a component to be loaded when that path is accessed

Then we make sure to import both `Routes` and `RouterModule`

`import { Routes, RouterModule } from '@angular/router';`

After importing the `RouterModule` we use the `forRoot` method, and pass in our route constant as an argument in the imports section of `@NgModule` like so:

`RouterModule.forRoot(appRoutes)`

We used the `<router-outlet>` directive in the `app.component.html` to specify where the component associated with the active route should be rendered

```
 </div>
  <div class="row">
    <div class="col-xs-12 col-sm-10 col-md-8 col-sm-offset-1 col-md-offset-2">
      <router-outlet></router-outlet>
    </div>
  </div>
```

with this, it will still load the app like it was normally already doing

This allows us to dynamically load different components based on the route accessed, creating a multi-page application with navigation between routes.

We still need to work on implementing links for navigation between routes, but those will be covered in the next the lesson
