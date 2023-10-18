# Setting up Child "Nested" Routes

In This video we created nested routes in our Angular application

Max shows us how implementing child routing with the `children` property in our route paths and using `<router-outlet></router-outlet>` in our html files we want to load, makes this approach a more dynamic routing behavior, because it help us organize and load child components within their parent components

To set up child or nested routes in our app, we first organize the routes in the following way in our `app.module.ts` :

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent, children: [
    { path: ':id/:name', component: UserComponent }
  ] },
  { path: 'servers', component: ServersComponent, children: [
    { path: ':id', component: ServerComponent },
    { path: ':id/edit', component: EditServerComponent }
  ] },
];
```

Since we had a list of routes with paths for users and servers, to nest them, we added the _children property_ to the UsersComponent and ServersComponent routes, and provided an array of nested routes inside them, _we removed the word users/ and servers/ from infront of the child paths because they are now always prepended_

When we nest routes, we also need a separate `<router-outlet></router-outlet>` for the child routes in the component's html files

In the `servers.component.html`, we comment out the existing code and add a <router-outlet> to create a new hook for loading child routes:

```
  <div class="col-xs-12 col-sm-4">
    <router-outlet></router-outlet>
    <!-- <button class="btn btn-primary" (click)="onReload()">Reload Page</button>
    <app-edit-server></app-edit-server>
    <hr> -->
    <!-- <app-server></app-server> -->
  </div>
```

Then for the UsersComponent, we also replaced `<app-user>` with another `<router-outlet>` in `users.component.html`:

```
  <div class="col-xs-12 col-sm-4">
    <!-- <app-user></app-user> -->
    <router-outlet></router-outlet>
  </div>
```
