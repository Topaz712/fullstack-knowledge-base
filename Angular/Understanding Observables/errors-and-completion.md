# Errors & Completion

Max discusses the key concepts about handling custom observables, including emitting data, handling errors, and completing the observable

_Observables are primarily used to emit new data_

- When subscribing to an observable, the first argument is used to specify the function that processes the emitted data

In the example code, _setInterval_ is used to emit values with the `observer.next(count);` method

in `home.component.ts`:

```
    const customIntervalObservable = Observable.create(observer => {
      let count = 0;
      setInterval(handler: () => {
        observer.next(count);
        if (count === 2) {
          observer.complete();
        }
        if (count > 3) {
          observer.error(new Error(message: 'Count is greater 3!'));
        }
        count++;
      }, timeout: 1000);
    });

    this.firstObsSubscription = customIntervalObservable.subscribe(data => {
      console.log(data);
    }, error => {
      console.log(error);
      alert(error.message);
    }, () => {
      console.log('Completed!');
    });
  }
```

- Handling errors is crucial, especially in scenarios like HTTP requests
  - We can simulate an error by checking a condition like `(count > 3)` and using `observer.error(new Error((message: 'Count is greater 3!'))` to throw an error
  - Subscribing to the observable's second argument allows us to handle errors
    - We can log the error, display it in an alert, or perform any desired error handling

**Completing an observable is different from throwing an error**

- By calling `observer.complete();` we manually complete the observable
  - When an observable completes, no more values are emitted

**It's important to understand that completion doesn't trigger the error handling function**

- To respond to completion, we can add a third argument when subscribing to the observable, by providing a function to handle the completion aka _completion handler function_ event like console logging "completed" `() => { console.log('Completed!');`

When an error occurs, the observable is canceled, but it doesn't complete

An observable can complete manually by calling observer.complete()

The completion handler does not execute in the case of an error, which shows that error handling and completion are separate events
