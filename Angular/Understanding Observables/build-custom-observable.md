# Building a Custom Observable

In this lesson, Max shows us how to build a custom observable from scratch in Angular

- To create a custom observable, we can use the rxjs library
  - we import the Observable class from rxjs and use the create method to build our own observable
  - When creating the observable, we pass a function that receives an observer as an argument
    - The observer is responsible for listening to new data, errors, and completion of the observable

Inside the function, we use regular JavaScript methods like setInterval, to emit new values using the observer's next method
in `home.component.ts`:

```
import { Subscription, interval, Observable } from 'rxjs';

export class HomeComponent implements OnInit, OnDestroy {

  private firstObsSubscription: Subscription;

  constructor() { }

  ngOnInit() {
    // this.firstObsSubscription = interval(1000).subscribe(count => {
    //   console.log(count);
    // });
    const customIntervalObservable = Observable.create(observer => {
      let count = 0;
      setInterval(handler: () => {
        observer.next(count);
        count++;
      }, timeout: 1000);
    });

    this.firstObsSubscription = customIntervalObservable.subscribe(data => {
      console.log(data);
    })
  }
    ngOnDestroy(): void {
    this.firstObsSubscription. unsubscribe();
  }
}
```

We also handle errors using the observer's error method and signal completion with the complete method

- It's important to subscribe to our custom observable to start receiving data
  - We should remember to store our subscription and unsubscribe when leaving the component to prevent memory leaks
