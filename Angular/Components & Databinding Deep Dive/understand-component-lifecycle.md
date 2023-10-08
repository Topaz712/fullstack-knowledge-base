# Understanding the Component Lifecycle

## ngOnChanges

- Called after a bound input property changes
- This hook is triggered whenever the value of a bound input property, decorated with `@Input` changes, it provides information about the changes

## ngOnInit

- Called once the component is initialized
- This hook is executed after Angular has initialized the component's properties but before it's added to the DOM, it's suitable for initial setup and data retrieval

## ngDoCheck

- Called during every change detection run
- Angular invokes this hook frequently during change detection, it's useful for custom change detection logic but should be used carefully due to its frequency

## ngAfterContentInit

- Called after content `ng-content` has been projected into the view
- This hook is triggered once the projected content from `ng-content` has been inserted into the component's view, it's often used when dealing with content projection

## ngAfterContentChecked

- Called every time the projected content has been checked
- This hook runs whenever Angular checks the projected content for changes, use when we need to perform operations after content updates

## ngAfterViewInit

- Called after the component's view and child views has been initialized
- This hook is executed when the component's view has been created, including any child views
  - It's suitable for DOM-related operations and interacting with child components

## ngAfterViewChecked

- Called every time the view and child views has been checked
- Angular invokes this hook after every check of the component's view and child views
  - Use for tasks that should run after each check

## ngOnDestroy

- Called once the component is about to be destroyed
- This hook is triggered just before Angular destroys the component
  - It's used for cleaning up resources, unsubscribing from observables, and performing other cleanup tasks
- These lifecycle hooks allow us to control the behavior of Angular components at various stages, making it possible to customize and optimize component functionality
