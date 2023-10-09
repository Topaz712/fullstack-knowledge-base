# Building a Structural Directive

To create a custom structural directive, which is the opposite of `*ngIf`, We create a directive with the CLI and name our directive "unless" so `unless.directive.ts`, and it will attach content only when the provided condition is false because `*ngIf` is only if the condition is true

To implement this, we use the `@Input` decorator to receive the condition as a boolean input

We create a setter method for the unless property, which gets executed whenever the condition changes

- Then inside this method, we check if the condition is false, and if so, we used `ViewContainerRef` to display the content provided by an `ng-template` If the condition is true, we cleared the view container, ensuring that nothing is displayed

```
<div *appUnless="onlyOdd">
  <li
  class="list-group-item"
  [ngClass]="{odd: even % 2 !== 0}"
  [ngStyle]="{backgroundColor: even % 2 !== 0 ? 'yellow' : 'transparent'}"
  *ngFor="let evenNumber of evenNumbers">
  {{ even }}
</li>
</div>

```

- This custom structural directive allows us to conditionally display content based on the provided condition, providing flexibility in our Angular applications

and we have to make sure property name in the `unless.directive.ts` shares the same name as the selector, so we change unless to appUnless in the TypeScript file

in the `unless.directive.ts`:

```
import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[appUnless]'
})
export class UnlessDirective {
  @Input() set appUnless(condition: boolean) {
    if (!condition) {
      this.vcRef.createEmbeddedView(this.templateRef);
    } else {
      this.vcRef.clear();
    }
  }

  constructor(private templateRef: TemplateRef<any>, private vcRef: ViewContainerRef) { }
}
```
