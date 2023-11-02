# Pure and Impure Pipes (or: How to "fix" the Filter Pipe)

In the last video, we made a filter pipe to sort servers by their status but when adding a new server while the filter was on, there was a problem because by defualt Angular doesn't refresh the pipe when data changes, for better performance

In _app.component.ts_:

```
onAddServer() {
    this.servers.push({
      instanceType: 'small',
      name: 'New Server',
      status: 'stable',
      started: new Date(15,1,2017)
    });
  }
```

In _app.component.html_:

```
<input type="text" [(ngModel)]="filteredStatus">
<br>
<button class="btn btn-primary" (click)="onAddServer()">Add Server</button>
<hr>
<ul class="list-group">
```

- To force the pipe to recalculate when data changes in the Application, we can set the pure property in the pipe decorator of our typescript to false
  - This will make the pipe recalculate when any data on the page changes
    - To be precise: updating arrays or objects doesn't trigger it
  - It's a powerful feature but it can impact performance, especially with large data lists so we have to use it cautiously

In _filter.pipe.ts_:

```
@Pipe({
  name: 'filter',
  pure: false
})
```

**So basically by default, Angular doesn't re-run pipes when the data changes for performance reasons which is good and setting the pure property to false in the pipe decorator forces the pipe to recalculate when data changes**
