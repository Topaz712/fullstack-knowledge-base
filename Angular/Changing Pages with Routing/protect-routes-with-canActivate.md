# Protecting Routes with canActivate

In this video lesson, we create a route guard to protect specific routes

- Route guards allow us to run code at specific times during the Angular app's routing process

Angular router offers a feature called _guards_ that allow us to protect certain actions, enabling us to run code when navigating routes, such as before a route is loaded or when leaving it

We start by creating a new service file `auth-guard.service.ts` in our app root folder and name it _AuthGuard_ because guards are used to protect routes by guarding certain actions
`export class AuthGuard implements CanActivate {}`

- In the AuthGuard class, we implement the _CanActivate_ interface provided by the Angular router package
  - This interface enforces the presence of a _canActivate method_ which accepts an `ActivatedRouteSnapshot` and the `RouterStateSnapshot` as arguments
  - Then we import necessary dependencies

```
canActivate(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot)
```

- The _canActivate method_ can return an observable 'wrapped in an Observable,' a promise, or a boolean value, to handle Observables we need to import 'Observable' from rxjs, `import { Observable } from "rxjs/Observable";`
  Observable is the correct path in this case in the video
  - Since it runs both, we can use these return types to run our guard code synchronously or asynchronously

Then we have to implement our guard logic, like checking whether a user `isAuthenticated` we use a promise to simulate an asynchronous process, and the guard navigates the user away if not authenticated

So we also create `auth.service.ts` :

```
export class AuthService {
  loggedIn = false;

  isAuthenticated() {
    const promise = new Promise(
      (resolve, reject) => {
        setTimeout(() => {
          resolve(this.loggedIn)
        }, 800);
      }
    );
  }

  login() {
    this.loggedIn = true;
  }
  logout() {
    this.loggedIn = false;
  }
}

```

Then to use the guard, we go to our route or routes including child routes, we want to protect, and add the _CanActivate property_ to them, so we specify our AuthGuard in the `app.module.ts` so import and provide the new _AuthGuard and any related services like AuthService as well_ in app.module.ts and in the providers array
by importing

```
import { AuthService } from './auth.service';
import { AuthGuard } from './auth-guard.service';
```

and
`providers: [ServersService, AuthService, AuthGuard],`

Now when we navigate to routes protected by the guard, it will only allow us access if the _canActivate method returns true_ making the /servers route and its child routes protected by the AuthGuard

in `auth-guard.service.ts`:

```
import {
  ActivatedRouteSnapshot,
  CanActivate,
  Router,
  RouterStateSnapshot
} from "@angular/router";
import { Observable } from "rxjs/Observable";
import { Injectable } from "@angular/core";

import { AuthService } from "./auth.service";

@Injectable()
export class AuthGuard implements CanActivate {
  constructor(
    private authService: AuthService,
    private router: Router) { }

  canActivate(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot): Observable<boolean> | Promise<boolean> | boolean {
      return this.authService.isAuthenticated()
        .then(
          (authenticated: boolean) => {
            if (authenticated) {
              return true;
            } else {
              this.router.navigate(['/']);
            }
          }
        );
    }
}

```

**So basically, we create route guards to protect routes based on certain conditions, making your application more secure and controlling access as needed**
