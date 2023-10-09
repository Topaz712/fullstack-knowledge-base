# ngClass and ngStyle Recap

## ngClass

- `[ngClass]` is a directive used to dynamically apply CSS classes to HTML elements based on conditions or expressions and this allows us to change the styling of elements dynamically
  - To use it we bind it to an expression that evaluates an object, where keys are class names and values are conditions that determine when those classes should be applied
- It is used for scenarios like conditional styling, toggling classes based on user interactions, or dynamically applying themes

for example in Max's video:

```
<div *ngIf="onlyOdd">
          <li
          class="list-group-item"
          [ngClass]="{odd: odd % 2 !== 0}"
          [ngStyle]="{backgroundColor: odd % 2 !== 0 ? 'yellow' : 'transparent'}"
          *ngFor="let oddNumber of oddNumbers">
          {{ odd }}
        </li>
```

## ngStyle

- `[ngStyle]` is a directive used to apply inline CSS styles to HTML elements dynamically, this allows us to modify element styles based on conditions or expressions
- It's commonly used for dynamic styling, like changing text color, font size, or background color based on user preferences or application states, like for odd and even in the video:

```
<div *ngIf="!onlyOdd">
          <li
          class="list-group-item"
          [ngClass]="{odd: even % 2 !== 0}"
          [ngStyle]="{backgroundColor: even % 2 !== 0 ? 'yellow' : 'transparent'}"
          *ngFor="let evenNumber of evenNumbers">
          {{ even }}
        </li>
        </div>
```

## Combined

They enable dynamic styling, enhancing the flexibility & interactivity of our Angular app

They allow us to respond to user actions, application state changes, or data conditions by modifying the appearance of elements in real-time

_Although they provide powerful styling capabilities, excessive use of these directives can impact the performance of our web app, so it's important to use them wisely and think about using regular CSS for styles that don't change often/static styles_
