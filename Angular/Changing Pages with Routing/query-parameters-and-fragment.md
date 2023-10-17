# Passing Query Parameters and Fragments

To pass query parameters and fragments in Angular, we can use both the _routerLink directive_ in the html templates and the _navigate method_ in our TypeScript code

So in the `app.module.ts` first we have to define the routes we will need :

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent },
  { path: 'users/:id/:name', component: UserComponent },
  { path: 'servers', component: ServersComponent },
  { path: 'servers/:id/edit', component: EditServerComponent },
];
```

Then in the `servers.component.html` we used the _routerLink directive to create links with dynamic parameter, query parameter, and a fragment_:

```
 <a
      [routerLink]="['/servers', 5, 'edit']"
      [queryParams]="{allowEdit: '1'}"
      fragment="loading"
        href="#"
        class="list-group-item"
        *ngFor="let server of servers">
        {{ server.name }}
      </a>
```

**queryParams property is not a directive it's just another bindable property of the routerLink directive**

So when we save and load the page we will now see `localhost:4200/servers/5/edit?allowEdit=1`
if we don't add fragment, but now with fragment, we get: `localhost:4200/servers/5/edit?allowEdit=1#loading`

For the same effect we will use the _navigate method_

So in our `home.component.html` we can pass 1 as an argument:

`<button class="btn btn-primary" (click)="onLoadServers(1)">Load Servers 1</button>`

Then in our `home.component.ts` we create a method to navigate programmatically:

```
  onLoadServers(id: number) {
    this.router.navigate(['/servers', id, 'edit'], {queryParams: {allowEdit: '1'}, fragment: 'loading'});
  }
```

So that is to use query parameters and fragments on both the programmatical routing approach with calling it from _the typescript code or on the routerLink of our html_, giving us flexibility to make our links more dynamic and interactive in our Angular app
