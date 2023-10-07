# Custom Property and Event Binding Summary

- Custom property and event binding are key features in Angular for component communication

- `@Input` allows us to make properties bindable from outside a component, enabling parent components to pass data to child components

- `@Output` enables parent components to listen to custom events created with `new EventEmitter`, allowing easy communication from child to parent components
  - These features are essential for creating dynamic and interactive Angular applications
    - They enable different components to interact and share data, enhancing the flexibility and functionality of our apps

While these features are powerful, complex chains of `@Input` and `@Output` can come up when components are closely connected, making communication more intricate/complicated

Max say's that in the service section of the course, an alternative approach to component communication will be introduced

- This alternative is better suited for scenarios where complex chains of inputs and outputs may not be practical, offering a more efficient solution

Custom property and event binding are essential tools for component communication in Angular, and we'll use them frequently in the course to build dynamic and interactive applications
