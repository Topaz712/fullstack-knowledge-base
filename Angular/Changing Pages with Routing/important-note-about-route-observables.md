# An Important Note about Route Observables

In the previous lecture, we learned how to subscribe to route observables to handle parameter changes reactively

- In the background, Angular handles the cleanup of subscriptions automatically when a component is destroyed, this ensures we don't have to manually unsubscribe from observables

Since Angular takes care of the subscription management for route observables in the background, we wouldn't need to implement additional code for this specific case:
in user.component.ts

```
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

- When we work with our own custom observables, especially those that are not related to route parameters, we'll need to manually unsubscribe when a component is destroyed

  - For manual unsubscribing, we would implement the `OnDestroy` lifecycle hook by importing it from @angular/core

  * Then we create a property to store the subscription, and once a component is destroyed, we can access the 'subscription' and unsubscribe as needed, but for route parameters, Angular takes care of it automatically

    in user.component.ts:

```
import { Component, OnDestroy, OnInit } from '@angular/core';
import { ActivatedRoute, Params } from '@angular/router';
import { Subscription } from 'rxjs/Subscription';

@Component({
  selector: 'app-user',
  templateUrl: './user.component.html',
  styleUrls: ['./user.component.css']
})
export class UserComponent implements OnInit, OnDestroy {
  user: {id: number, name: string};
  paramsSubscription: Subscription;

  constructor(private route: ActivatedRoute) { }

  ngOnInit() {
    this.user = {
      id: this.route.snapshot.params['id'],
      name: this.route.snapshot.params['name']
    };
    this.paramsSubscription = this.route.params
      .subscribe(
        (params: Params) => {
          this.user.id = params['id'];
          this.user.name = params['name'];
        }
      );
  }

  ngOnDestroy(): void {
    this.paramsSubscription.unsubscribe();
  }
}

```

- The paramsSubscription is a property of type Subscription used to manage a subscription to route parameters in Angular
  - To use the Subscription type, we need to import it from `'rxjs/Subscription'`, this type is part of the _Rxjs library_, which is used for managing observables and asynchronous operations

_Angular automatically cleans up subscriptions for route observables for route parameters when a component is destroyed, when the component is destroyed, Angular takes care of managing and cleaning up these subscriptions when we subscribe to route parameters using `this.route.params.subscribe()` but we will need to manually unsubscribe from custom observables, which is important otherwise it could lead to memory leaks_

- Initially, `this.route.snapshot.params` is used to retrieve parameters when the component loads
  - Then the `this.route.params.subscribe()` subscription reacts to changes in route parameters
  - The `this.paramssubscription` is used to reactively update the user object when route parameters change

This code ensures that when route parameters change, the user object is also updated accordingly, and so Angular automatically manages the cleanup of the subscription when the component is destroyed
