# Fetching Route Parameters Reactively

In the previous lecture, we learned to retrieve route parameters using the `.snapshot` object from `ActivatedRoute`, It works fine initially, but we need a more robust approach to handle dynamic changes in route parameters.

An example of this is with the "users" component in our `user.component.html`, routerLink is added with an array that constructs a URL with parameters, the link changes the URL when we click, but the component doesn't reload

```
<p>User with ID {{ user.id }} loaded.</p>
<p>User name is {{ user.name }}</p>
<hr>
<a [routerLink]="['/users', 10, 'Anna']">Load Anna (10)</a>

```

With the default behavior Angular doesn't reload a component if we're already on it, so while this is efficient, it doesn't automatically update data when parameters change

To handle parameter changes reactively, we need to use observables, _the params property of the route object is an observable that emits parameter changes_

To access route parameters as an observable, you can use the params property from the route object and subscribe to it.

```
};
    this.route.params
      .subscribe(
        (params: Params) => {
          this.user.id = params['id'];
          this.user.name = params['name'];
        }
      );
```

- So when we subscribe to the params observable, we essentially define a function that will execute whenever the parameters change, which in turn, this function receives the updated parameters as an argument
  - We subscribe to the params observable to listen for parameter changes, and when parameters change, the subscription function is then executed

Inside the subscription function, we can update our component's properties based on the changed parameters, this makes sure that our component stays in sync with parameter updates

When we use observables, it ensures that our component reflects the most up-to-date parameter values, and best practice for handling route parameter changes

- It is a best practice to use the observable-based approach to react to route parameter changes in your Angular application.
  - But if our component will always be recreated when reached like if it has no way of reaching it without reloading, then we can stick with the snapshot, Otherwise we should use observables to handle parameter changes effectively because it ensures that our component always reflects the most up-to-date data

In user.component.ts:

```
import { Component, OnInit } from '@angular/core';
import { ActivatedRoute, Params } from '@angular/router';

@Component({
  selector: 'app-user',
  templateUrl: './user.component.html',
  styleUrls: ['./user.component.css']
})
export class UserComponent implements OnInit {
  user: {id: number, name: string};

  constructor(private route: ActivatedRoute) { }

  ngOnInit() {
    this.user = {
      id: this.route.snapshot.params['id'],
      name: this.route.snapshot.params['name']
    };
    this.route.params
      .subscribe(
        (params: Params) => {
          this.user.id = params['id'];
          this.user.name = params['name'];
        }
      );
  }
```
