# Using HostListener to Listen to Host Events

In this lesson, we learned how to enhance our attribute directives to make them more interactive by using the `@HostListener` decorator

- This decorator allows us to listen for specific events that happen on the element where the directive is used, so we specify the event name as an argument in the decorator as a string

```
@HostListener('mouseenter') mouseover(eventData: Event) {
this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'blue', false, false);
}

@HostListener('mouseleave') mouseleave(eventData: Event) {
this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'transparent', fasle, false);
}

```

We added a `mouseenter` event listener that changes the background color to _blue_ when the mouse enters the element and added a `mouseleave` event listener that sets the background color to _transparent_ when the mouse leaves the element

These event listeners use the Renderer to modify the element's styles, making sure it works well in different situations
