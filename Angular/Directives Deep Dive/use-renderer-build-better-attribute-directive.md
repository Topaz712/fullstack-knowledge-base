# Using the Renderer to build a Better Attribute Directive

- In this lesson, we learn that directly accessing elements in Angular directives, like in the previous lesson, is not considered good practice
  - This is because Angular can render templates without a DOM, and in such cases, direct DOM access may not work correctly
  - To handle DOM access more effectively, we should use the `Renderer2` service, which is provided by Angular
  - This approach is considered better because it allows Angular to manage DOM manipulation more strongly

To implement this, a new directive called `BetterHighlightDirective` is created using Angular CLI's ng generate directive command `ng g directive` or also `ng g d` then directive name of your choice
This directive injects the `Renderer2` service alongside the `ElementRef` service, The Renderer2 service provides methods to safely access and manipulate DOM elements

So once `BetterHighlightDirective` is created with the selector `[appBetterHighlight]`

in better-highlight.directive.ts:

```
import { Directive, OnInit, Renderer2, ElemenetRef } from '@angular/core';

@Directive({
selector: '[appBetterHighlight]'
})
export class BetterHighlightDirective implements OnInit {

constructor(private elRef: ElementRef, private renderer: Renderer2) { }

ngOnInit() {
this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'blue')
}
}
```

The directive's `ngOnInit()` method uses the `renderer2` to set the background color of the element to blue, this is done by specifying the element reference and the desired style changes using the renderer's methods

in app.component.html:
`<p appBetterHighlight>Style me with better directive!</p>`

_This improved approach ensures that DOM access is done correctly, even in environments like service workers where direct access may not be available_

- **So basically in this video lesson, Max suggests using a tool called "renderer2" in Angular to work with web page elements, this helps make sure our code works well in various environments/situations and prevents potential problems that can happen when we access/work directly with elements**
  - **This approach is seen as a better way to create attribute directives**
