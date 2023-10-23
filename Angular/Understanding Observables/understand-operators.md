# Understanding Operators

**Operators in rxjs are a crucial feature that enhances observables**

- They allow us to transform, filter, and manipulate data

  - Instead of doing these operations within our subscription function, we can insert operators in between our observable and the subscription, creating a data transformation pipeline

- Operators are essential for working with observables

  - They provide powerful tools for transforming, filtering, and processing data

- We can use the pipe method to chain operators together in a sequence

- One common operator is map, which allows us to transform each emitted value in the observable

- Another useful operator is filter, which enables us to filter out values based on certain criteria

- Operators can significantly simplify and enhance our code when working with observables

The RxJS library includes numerous built-in operators for various data manipulation tasks

If we want to look at it more we can go to [learnrxjs.io](https://www.learnrxjs.io/learn-rxjs/operators) and learn more

in `home.component.ts`:

```
import { map, filter } from 'rxjs/operators'

    this.firstObsSubscription =     customIntervalObservable.pipe(filter(data => {
      return data > 0;
    }), map((data: number) => {
      return 'Round: ' + (data + 1);
    })).subscribe(data => {
      console.log(data);
    }, error => {
      console.log(error);
      alert(error.message);
    }, () => {
      console.log('Completed!');
    });
  }
```
