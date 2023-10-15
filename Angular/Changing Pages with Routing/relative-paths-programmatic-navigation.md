# Using Relative Paths in Programmatic Navigation

If we use a method in out `servers.component.ts`

```
onReload() {
    this.router.navigate(['servers']);
  }
```

For our button in our `servers.component.html`:

```
    <button class="btn btn-primary" (click)="onReload()">Reload Page</button>
```

- Programmatic navigation using router navigate allows us to navigate to a different route in our Angular app

If we use a relative path in the navigate method and if we're currently on the "servers" component, it appends the path relative to the current component's route

- Unlike `routerLink`, the navigate method doesn't naturally know the current route so to specify the relative path correctly, we need to provide the navigation context by passing an extra argument which is a JavaScript object like so:

```
  onReload() {
    // this.router.navigate(['servers'], {relativeTo: this.route});
  }//but we commented it out because there is no servers/servers so it will not work and break the app
```

In this object, we set the relativeTo property to the route we wanted to navigate relative to, because by default, it's relative to the root domain

We can access the currently active route by injecting `ActivatedRoute` in our constructor:
`import { Router, ActivatedRoute } from '@angular/router';`

```
  constructor(
    private serversService: ServersService,
    private router: Router,
    private route: ActivatedRoute) { }
```

The `relativeTo` property defines the route to which the path should be relative

Then we just ned to make sure to import both Router and ActivatedRoute from the @angular/router package

This is why it's important to know how relative paths work in the navigate method, because we can control the context of the navigation in our Angular app
