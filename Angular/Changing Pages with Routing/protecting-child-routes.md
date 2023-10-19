# Protecting Child (Nested) Routes with canActivateChild

To protect child 'nested' routes, we can use the _canActivateChild guard_ which is similar to _canActivate_

To implement the `CanActivateChild` interface in our `auth-guard.service.ts` we import it from @angular/router and add it to the class as well:

```
import { CanActivate, CanActivateChild } from "@angular/router";

@Injectable()
export class AuthGuard implements CanActivate, CanActivateChild {
```

In the _AuthGuard class_ we add the _canActivateChild method_ which is set the same way as _canActivate_

- It takes route and state as arguments and can return an observable, promise, or boolean value:

```
canActivateChild(
  route: ActivatedRouteSnapshot,
  state: RouterStateSnapshot):
    Observable<boolean> | Promise<boolean> | boolean {
      return this.canActivate(route, state);
    }
}
```

Now we can use _canActivateChild_ in our routes in the place of 'canActivate' because it provides fine-grained control over child routes
To implement it in our route configuration we comment out canActivate and use `canActivateChild: [AuthGuard]` instead so
in `app-routing.module.ts`:

```
{ path: 'servers',
    // canActivate: [AuthGuard],
    canActivateChild: [AuthGuard],
    component: ServersComponent,
    children: [
    { path: ':id', component: ServerComponent },
    { path: ':id/edit', component: EditServerComponent }
  ] },
```

With this set up like this, child routes under the 'servers' route are now protected, and the 'AuthGuard' can work with both protecting the parent route and all its child routes or only the child routes based on our app's requirements/behavior
