# Controlling Navigation with canDeactivate

This video lesson focuses on controlling whether we're allowed to leave a route

For this we'll use `CanDeactivate` , in the context of editing a server, we want to ask the user if they're sure they want to leave, especially if they made changes

- To implement _CanDeactivateGuard_ we created a new service file called `can-deactivate-guard.service.ts`
  - This will be a service, as all guards are

Then we export an interface called `CanComponentDeactivate`, an interface simply is a contract which can be imported by some of our class, so it forces the class to implement a _canDeactivate method that returns an Observable, Promise, or Boolean_

So we implement the _CanDeactivate interface by creating a class CanDeactivateGuard_ and will have a canDeactivate method

in `can-deactivate-guard.service.ts`:

```
import { Observable } from "rxjs/Observable";
import {
  CanDeactivate,
  ActivatedRouteSnapshot, RouterStateSnapshot } from '@angular/router'

export interface CanComponentDeactivate {
  canDeactivate: () => Observable<boolean> | Promise<boolean> | boolean;
}

export class CanDeactivateGuard implements<CanComponentDeactivate> {

  canDeactivate(
    component: CanComponentDeactivate,
    currentRoute: ActivatedRouteSnapshot,
    currentState: RouterStateSnapshot,
    nextState?: RouterStateSnapshot): Observable<boolean> | Promise<boolean> | boolean {
      return component.canDeactivate();
    }
}

```

- In the canDeactivate method, the guard checks if the user made changes that haven't been saved

- If changes are made and not saved, it prompts the user with a confirmation dialog
  - If no changes were made or they were saved, it returns true to allow navigation or otherwise, it returns false

Now in the route configuration of `app-routing.module.ts` we add CanDeactivate as a property along with the CanActivate property

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent, children: [
    { path: ':id/:name', component: UserComponent }
  ] },
  { path: 'servers',
    // canActivate: [AuthGuard],
    canActivateChild: [AuthGuard],
    component: ServersComponent,
    children: [
    { path: ':id', component: ServerComponent, resolve: {server: ServerResolver} },
    { path: ':id/edit', component: EditServerComponent, canDeactivate: [CanDeactivateGuard] }
  ] },
```

This will then tell Angular to use this guard when leaving the specified route

In the component where we want to control navigation, the `edit-server.component.ts`, we implement the _CanComponentDeactivate interface_

```
canDeactivate(): Observable<boolean> | Promise<boolean> | boolean {
    if (!this.allowEdit) {
      return true;
    }
    if ((this.serverName !== this.server.name || this.serverStatus !== this.server.status) && !this.changesSaved) {
      return confirm('Do you want to discard the changes?');
    } else {
      return true;
    }
  }
```

We implement the _canDeactivate method_ to provide logic based on changes and whether they've been saved

- Now, when a user tries to leave the edit server route after making unsaved changes, a confirmation dialog appears
  - If they confirm, they can leave and if they cancel, they remain on the page to save their changes

**So basically, the `CanDeactivate guard` provides an additional layer of protection, ensuring users don't accidentally lose unsaved data**
