# Binding to Custom Properties

In this video Max is explaining the `serverElements` property in `app.component.ts`, which manages an array of server elements, so he uses JavaScript object syntax to populate the `serverElements` property:

In this example, `serverElements` is an array of JavaScript objects:

```
export class AppComponent {
  serverElements =[{type: 'server', name: 'Testserver', content: 'Just a test!'}];

}
```

Since we're on the right side of the equal sign so here we are assigning a value

- The colons `:` in the object definition are not type definitions but key-value pairs in JavaScript

- Because the object in the array contains key-value pairs, where keys represent property names like "type, name, and content", and values hold the corresponding data for those names.

In the next part of the video we want to bind to the `serverElements` property defined in `server-element.component.ts` to have in our `app.component.html` :

```
<div class="container">
<app-cockpit></app-cockpit>
  <hr>
  <div class="row">
    <div class="col-xs-12">
      <app-server-element
      *ngFor="let serverElement of serverElements"
      [element="serverElements"]></app-server-element>
    </div>
  </div>
</div>
```

When we first try it just like in the example above, it doesn't work becuase **By default, component properties are only accessible inside the component itself, which is a good thing because we don't want to make all our properties bindable from outside**

- To allow parent components to bind to a property, we need to explicitly expose it using the `@Input()`` decorator
  - The `@Input()` decorator should be applied to the property we want to make bindable

_Decorators are not only available for classes_

- In the `ServerElementComponent` component, the element property we mark with `@Input()` to make it accessible from outside
  - Then we must import the @Input decorator from '@angular/core' like so :

```
import { Component, OnInit, Input } from '@angular/core';

@Component({
selector: 'app-server-element',
templateUrl: './server-element.component.html',
styleUrls: ['./server-element.component.css']
})
export class ServerElementComponent implements OnInit {
@Input() element: {type: string, name: string, content: string};

constructor() { }

ngOnInit() { }

}
```

We add parenthesis to execute it, it's like a function in the end

**So basically, using `@Input()` decorators, we can expose and bind custom properties in Angular components, enabling parent components to interact with and pass data to child components**
