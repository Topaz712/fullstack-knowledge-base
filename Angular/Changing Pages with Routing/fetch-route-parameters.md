# Fetching Route Parameters

To access data sent through a URL or encoded in a dynamic path segment, in `user.component.ts` will have to do:

```
  constructor(private route: ActivatedRoute) { }

  ngOnInit() {
    this.user = {
      id: this.route.snapshot.params['id'],
      name: this.route.snapshot.params['name']
    };
  }
```

To access this data, we inject the `ActivatedRoute` object in our component's constructor and import it so:
`import { ActivatedRoute } from '@angular/router';`

- _The ActivatedRoute object provides information about the currently loaded route, including any parameters_

  - _We can access parameters by using the `snapshot.params` property of the ActivatedRoute object_
    - _It's an object where we can retrieve parameter values based on their names, such as id and name_

**To avoid confusion: the ActivatedRoute object we injected in the constructor will give us access to the ID passed in the URL => Selected User**

- Now that we Modified our routes in the `app.module.ts`, we set up dynamic path segments, these segments can be named parameters that hold data, like 'id' and 'name'

in app.module.ts:

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent },
  { path: 'users/:id/:name', component: UserComponent },
  { path: 'servers', component: ServersComponent },
];
```

- In our component's `ngOnInit` method, we retrieve the values of these parameters and use them in our component, in the video the 'id' and 'name' parameters are used to set properties of the user object

Now we can use the data in the `user.component.html` using string interpolation like so:

in user.component.html:

```
<p>User with ID {{ user.id }} loaded.</p>
<p>User name is {{ user.name }}</p>
```

The `routerLinkActive` directive continues to function as expected, highlighting the active links based on the current route in our app

So basically we can extract data from the URL and use it dynamically inside our Angular components by injecting `ActivatedRoute` and accessing route parameters
