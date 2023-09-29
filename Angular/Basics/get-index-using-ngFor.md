# Getting the index when using ngFor

```
<div
  *ngFor="let logItem of log; let i = index"
>
```

Equal to index is kind of like a reserved expression, it gives us access to the _index of the current iteration_

- The index will start at zero

**`*ngFor` is useful if we want to be able to easily get the position or index of items in a list and display them on our web page**

_It helps us repeat something multiple time on our web page_
