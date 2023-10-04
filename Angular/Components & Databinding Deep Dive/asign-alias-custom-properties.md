# Assigning an Alias to Custom Properties

- In Angular, we can bind to custom properties using the `@Input()` decorator without parentheses
  - Because sometimes we may want to use a different property name outside the component than inside of it

For example in our app.component.html we might not want to use `element`

```
<div class="col-xs-12">
      <app-server-element
      *ngFor="let serverElement of serverElements"
      [element="serverElements"]></app-server-element>
    </div>
```

Instead if we want to bind to `srvElement`

```
      <app-server-element
      *ngFor="let serverElement of serverElements"
      [srvElement="serverElements"]></app-server-element>
```

to make it clear it's a server element then we would need to assign an alias in our `server-element.components.ts`

**We can assign an alias to a custom property by providing an argument to `@Input()` with the desired property name for external use**

- When we define `@Input('srvElement') element`, it allows us to bind to `srvElement` from outside the component
  - Inside the component, we continue to use the original property name, which in this case, is `element`

```
export class ServerElementComponent implements OnInit {
  @Input('srvElement') element: {type: string, name: string, content: string};

  constructor() { }

  ngOnInit() { }

}
```

**When we bind to the property from outside the component, we need to use the alias `srvElement` to access the property, rather than the internal property name `element` because it will no longer work outside**

_So basically assigning an alias helps make property binding more expressive and clear for external use, making our code more readabable and easy to understand_
