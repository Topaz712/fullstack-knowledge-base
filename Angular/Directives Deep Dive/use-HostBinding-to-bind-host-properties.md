# Using HostBinding to Bind to Host Properties

In this video lesson, we learned about the `@HostBinding` decorator, which is a more convenient way to modify an element's properties within a directive

With `@HostBinding` we can directly bind to a property of the element we're sitting on

To use the `@HostBinding` decorator we follow it parentheses and inside the parentheses, we use a string that specifies the property of the hosting element we want to bind to

So we use `style.backgroundColor` and this will allow us to bind to the background color property of the element's style

Then we initialize the bound property with a default value like `transparent` for background color

Now, we can modify this property directly within the directive without needing the Renderer

```
export class BetterHighlightDirective implements OnInit {
@HostBinding('style.backgroundColor') backgroundColor: string = 'transparent';

constructor(private elRef: ElementRef, private renderer: Renderer2) { }

ngOnInit() {
// this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'blue');
}

@HostListener('mouseenter') mouseover(eventData: Event) {
// this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'blue', false, false);
this.backgroundColor = 'blue';
}
@HostListener('mouseleave') mouseleave(eventData: Event) {
// this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'transparent', fasle, false);
this.backgroundColor = 'transparent';
}
}
```

We used `@HostBinding` to bind to the `style.backgroundColor` property, which allowed us to change the background color of the element when hovering over it without using the Renderer

This simplifies the code and provides a more straightforward way to work with element properties inside a directive
