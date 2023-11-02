# Understanding the "async" Pipe

- The `async pipe` is distinct from other pipes
  - It is designed to handle asynchronous data, such as Promises or Observables

In _app.component.ts_:

```
  appStatus = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('stable');
    }, 2000);
  });
```

We created a property named `appStatus` that contains a _Promise_ with a two second delay and when we use the _async pipe_ in our html template, it will automatically update the displayed value when the Promise resolves

In _app.component.html_:

```
<button
  class="btn btn-primary"
  (click)="onAddServer()"
  >Add Server
</button>
<br><br>
<h2>App Status: {{ appStatus | async }}</h2>
```

The `async pipe` is a handy tool for managing asynchronous data, ensuring that Angular recognizes and reflects changes when the data becomes available
