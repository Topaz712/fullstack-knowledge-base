# Retrieving Query Parameters and Fragments

In this video lesson we go over how we can access our query parameters and fragments using the ActivatedRoute

So in our `edit-server.component.ts` we import the package and then inject it into the constructor:

`import { ActivatedRoute } from '@angular/router';`

```
constructor(
    private serversService: ServersService,
    private route: ActivatedRoute) { }
```

_There are two ways to retrieve these query parameters and fragments_

The first approach is to use the snapshot property of our route in the ngOnInit method:

```
ngOnInit() {
    console.log(this.route.snapshot.queryParams);
    console.log(this.route.snapshot.fragment);
```

With this approach, it won't be reactive, so it won't update if the query parameters change after the component is loaded

The second approach is to use query params and fragment as observables and we can subscribe to them like so:

```
this.route.queryParams.subscribe();
this.route.fragment.subscribe();
```

- Unlike with the snapshot approach, we don't need to unsubscribe from these observables because Angular will handle the cleanup for us, just like it did for route parameters
  - This allows us to react to changes in query parameters and fragments

_These methods give us the ability to access and respond to these extra details while ensuring we don't miss any updates/changes_
