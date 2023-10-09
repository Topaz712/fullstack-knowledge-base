# Creating a Basic Attribute Directive

To create a basic attribute in Angular first, we inject the element the directive sits on into the directive class using the constructor and Angular handles this injection for us

So in `basic-highlight.directive.ts`:

```
import { Directive, ElementRef } from '@angular/core';

@Directive({
selector: '[appBasicHighlight]'
})

export class BasicHighlightDirective implements OnInit {
constructor(private elementRef: ElementRef) {
}

ngOnInit() {
this.elementRef.nativeElement.style.backgroundColor = 'green';
}
}

```

Just like components, directives have lifecycle hooks so we used the `ngOnInit() {}` hook to access the element and modify its style

Then to inform Angular about our custom directive, we need to declare it in the declarations array of our `app.module.ts` like so:

```
import { BasicHighlightDirective } from './basic-highlight/basic-highlight.directive';

@NgModule({
  declarations: [
    AppComponent,
    BasicHighlightDirective
```

Finally We used the directive in our `app.component.html` file by adding it as an attribute to an element, and it's important to note that we don't use square brackets when adding directives as attributes because they're not part of the name itself and instead it's "part of the selector style telling angular please select it as an attribute to an element"

In `app.component.html`:
`<p appBasicHighlight>Style me with basic directive!</p>`

Overall, this allowed us to create a basic attribute directive that styles an element when used in the HTML
