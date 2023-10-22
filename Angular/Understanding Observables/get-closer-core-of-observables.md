# Getting Closer to the Core of Observables

Observables in Angular are made possible by the RxJS library, and we can create custom observables when we need them for our application

- Observables are not native to JavaScript or TypeScript, they are added to these languages through a package called `rxjs`
  - If we look at `package.json` which lists all our dependencies, we will find `rxjs` there
- In our Angular projects, `rxjs` is a critical dependency, since Angular relies on it for handling observables
  - To create our own observable, we can use `rxjs` functions like `interval` or other observable creation methods

We don't usually need to create Observables from scratch in Angular, since many built-in ones are provided

in `home.component.ts`:

```
import { Component, OnDestroy, OnInit } from '@angular/core';
import { Subscription, interval } from 'rxjs';
import { count } from 'rxjs-compat/operator/count';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit, OnDestroy {

  private firstObsSubscription: Subscription;

  constructor() { }

  ngOnInit() {
    this.firstObsSubscription = interval(1000).subscribe(count => {
      console.log(count);
    })
  }

  ngOnDestroy(): void {
    this.firstObsSubscription. unsubscribe();
  }
}

```

In the video example, we created an observable using the interval function from the _rxjs library_ , this observable emitted values every second

**It's essential to unsubscribe from observables to prevent memory leaks and unnecessary resource consumption, Angular takes care of unsubscribing for its own observables, but for others, we should manually unsubscribe**

- The _ngOnDestroy lifecycle hook_ is a good place to perform the unsubscription
