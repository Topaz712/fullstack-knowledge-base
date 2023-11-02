# Example: Creating a Filter Pipe

**The `filter pipe` enables dynamic filtering of server data based on user input, improving the application's usability**

In _app.component.ts_:
`filteredStatus = '';`

- We use the Angular CLI to generate a new pipe file named **filter**
  - Here the _transform method_ will take three parameters: `value` - the array to filter, `filterString` - the user's filter input, and `propName` - the property to filter by like 'status'

In _filter.pipe.ts_:

```
  transform(value: any, filterString: string, propName: string): any {
    if (value.length === 0 || filterString === '') {
      return value;
    }
    const resultArray = [];
    for (const item of value) {
      if (item[propName] === filterString) {
        resultArray.push(item);
      }
    }
    return resultArray;
  }
```

In the transform method, it's checked if value is an array and if filterString is empty, in which case the unfiltered array is returned

- The `resultArray` is initialized to hold the filtered items

  - A loop iterates through each _item_ in the _value_ array and then items with `item[propName]` matching `filterString` are pushed to the `resultArray`

  * The `resultArray` is returned, containing the filtered items based on the provided property name and filter string given

- Now we will add an input field to allow users to filter a list of servers by status
  - Two way data binding is used to connect the input field to the filteredStatus property in the html component: `[(ngModel)]="filteredStatus"`

In _app.component.html_:

```
<input type="text" [(ngModel)]="filteredStatus">
      <hr>
      <ul class="list-group">
        <li
          class="list-group-item"
          *ngFor="let server of servers | filter:filteredStatus:'status'"
          [ngClass]="getStatusClasses(server)">
```

In template, the filter pipe is applied within the `*ngFor loop` to filter the list of servers

We pass two parameters to the filter pipe:
`filteredStatus and 'status'`

- In the video there was an issue where only the first item in a category was displayed, to fix this, in the _filter.pipe.ts_, the return statement was moved outside of the for loop, and the resultArray was also created outside of the loop to collect all the matching items
  - After that, the filter pipe worked as expected, allowing users to filter servers by status
  - An additional condition was added to handle the case when the filter string is empty, it would now show all servers

Even with this done, there is another issue Max mentions that will be fixed in the next video
