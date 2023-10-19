# Using a Fake Auth Service

To complete the canActivate demonstration Max was showing us, we can finish this fake auth service like so:

First we add two buttons in our home component for login and logout

in `home.component.html`:

```
<button
  class="btn btn-default"
  (click)="onLogin()">Login
</button>
<button
  class="btn btn-default"
  (click)="onLogout()">Logout
</button>
```

Now in the _home.component.ts_ file, we inject the **AuthService** in our constructor as well as import it, then create the methods

in `home.component.ts`:

```
import { AuthService } from '../auth.service';

constructor(
    private router: Router,
    private authService: AuthService) { }

onLogin() {
  this.authService.login();
}
onLogout() {
  this.authService.logout();
}
```

Now these buttons, when clicked, will invoke the login and logout methods from the AuthService
This simple addition enables us to visually verify the operation of the _canActivate guards_, with an automatic redirection delay 'it takes about 800 milliseconds to evaluate whether we are allowed acesss' after clicking 'Logout'
