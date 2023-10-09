# Understanding ngSwitch

The `ngSwitch` directive in Angular will allows us to conditionally display content based on a specific value

- In Max's video we added a div element with the `[ngSwitch]` property binding, where `[ngSwitch]` is bound to a variable called "value"
- This variable is going to essentially be our condition that we want to check

- Within the div, we used `*ngSwitchCase` to define different cases based on the possible values of value

We have cases for 5, 10, and 100, each case contains content that should be displayed when the condition matches the value

in app.component.html:

```
<div [ngSwitch]="value">
  <p *ngSwitchCase="5">Value is 5</p>
  <p *ngSwitchCase="10">Value is 10</p>
  <p *ngSwitchCase="100">Value is 100</p>
  <p *ngSwitchDefault>Value is default</p>
</div>
```

We also included an `*ngSwitchDefault` case, which shows content when none of the other cases apply

- By changing the value of the value variable in our component, we could dynamically switch between different cases, like if we set the value to 5 will display the "Value is 5" content

in app.component.ts:

```
export class AppComponent {
  numbers = [1, 2, 3, 4, 5];
  oddNumbers = [1, 3, 5];
  evenNumbers = [2, 4];
  onlyOdd = false;
  value = 5;
}
```

**So basically `ngSwitch` is a useful alternative to using multiple `*ngIf` conditions, especially when we have many possible cases to handle because it simplifies the template and improves readability**
