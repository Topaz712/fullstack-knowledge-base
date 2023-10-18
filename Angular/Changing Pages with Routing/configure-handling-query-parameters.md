# Configuring the Handling of Query Parameters

In the last lecture we improved our application a bit but the issue is our query parameters are gone in the url whenever we navigate away from a single server component

The issue is that query parameters disappear when navigating between components, and we want to keep this information even after moving to a different component

The way to preserve query parameters when navigating between components, is by configuring how they are handled in our application

To preserve query parameters when navigating from a single _server.component_ to an _edit-server.component_, we add a property called `queryParamsHandling` in the router of our _onEdit()_ method in the `server.component.ts`:
import from @angular/router:
`import { ActivatedRoute, Params, Router } from '@angular/router';`

inject router into constructor to use navigate:

```
 constructor(
    private serversService: ServersService,
    private route: ActivatedRoute,
    private router: Router) { }
```

```
 onEdit() {
    this.router.navigate(['edit'], {relativeTo: this.route, queryParamsHandling: 'preserve'});
  }
```

- The queryParamsHandling property is set to 'preserve,' which tells Angular to keep the old query parameters intact and not discard them

  - By using 'preserve,' existing query parameters aren't lost when navigating to another component, this is an essential technique to make sure we maintain query parameter information across component transitions, which is great for preserving user context and maintaining the integrity of our application's state, which in turn provides a seamless user experience

- If we were adding new query parameters, we might use 'merge' instead, which would merge the old and new parameters
