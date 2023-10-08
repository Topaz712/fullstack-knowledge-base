# Getting Access to the Template and DOM with @ViewChild

In Angular, we can access elements or components in the template directly from TypeScript code using the `@ViewChild` decorator

- To use `@ViewChild`, we apply it as a decorator to a TypeScript property, import it from @angular/core, and specify the element's selector
  - We can pass a string argument to `@ViewChild` with the name of a local reference to select an element

```
@Component({
  selector: 'app-cockpit',

  export class CockpitComponent implements OnInit {
  @Output('bpCreated') blueprintCreated = new EventEmitter<{serverName: string, serverContent: string}>();;
  // newServerName = '';
  // newServerContent = '';
  @ViewChild('serverContentInput') serverContentInput;
  @ViewChild('serverContentInput') serverContentInput: ElementRef;

   constructor() {}
```

- Unlike with local references, `@ViewChild` allows us to access elements before calling methods
  - The selector can be a local reference name as a string or a component type
    - We pass the local reference name as a string to `@ViewChild` to select the element we want to access

```
onAddBlueprint(nameInput: HTMLInputElement) {
    this.blueprintCreated.emit({
      serverName: nameInput.value,
      serverContent: this. newServerContent
      serverContent: this.serverContentInput.nativeElement.value
    });
```

Alternatively, we can select a component by passing its type and it's recommended for us to use tools like string interpolation and property binding for outputting content in the DOM rather than directly manipulating elements obtained through `@ViewChild`

_Avoid changing elements directly through the DOM_, as Angular provides better alternatives for interacting with the DOM, which will be covered in the directives section
