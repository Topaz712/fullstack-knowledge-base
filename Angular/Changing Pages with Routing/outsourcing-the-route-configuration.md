# Outsourcing the Route Configuration

As our application grows and we have more than two or three routes, it's good practice to move route configurations out of the _app.module.ts_ to keep code organized and maintainable

So we create a new file called `app-routing.module.ts` which will serve as a module specifically for routing and related tasks

Now in the `app-routing.module.ts` we define our routes using the Routes array and then cut and paste your routes from the `app.module.ts` and import the necessary components for our routes

Then we remove the router module imports from our app.module.ts to keep it cleaner/leaner

In the `app-routing.module.ts` we make the router module accessible to other modules by adding it to the exports array inside the _@NgModule decorator_
This allows other modules that import `app-routing.module` to use the router module we configured

in app-routing.module.ts:

```
import { NgModule } from "@angular/core";
import { Routes, RouterModule } from "@angular/router";

import { PageNotFoundComponent } from "./page-not-found/page-not-found.component";
import { EditServerComponent } from "./servers/edit-server/edit-server.component";
import { ServerComponent } from "./servers/server/server.component";
import { ServersComponent } from "./servers/servers.component";
import { UsersComponent } from "./users/users.component";
import { UserComponent } from "./users/user/user.component";
import { HomeComponent } from "./home/home.component";

const appRoutes: Routes = [
{ path: '', component: HomeComponent },
{ path: 'users', component: UsersComponent, children: [
{ path: ':id/:name', component: UserComponent }
] },
{ path: 'servers', component: ServersComponent, children: [
{ path: ':id', component: ServerComponent },
{ path: ':id/edit', component: EditServerComponent }
] },
{ path: 'not-found', component: PageNotFoundComponent },
{ path: '\*\*', redirectTo: '/not-found'}
];

@NgModule({
imports: [
RouterModule.forRoot(appRoutes)
],
exports: [RouterModule]
})
export AppRoutingModule {

}
```

Finally in `app.module.ts` we import our `app-routing.module.ts` in the imports array

- This approach keeps your app module cleaner/leaner and follows good practices for keeping code organized
  - The application functionality remains the same, but now our code is easier to read and manage as it grows more complex
