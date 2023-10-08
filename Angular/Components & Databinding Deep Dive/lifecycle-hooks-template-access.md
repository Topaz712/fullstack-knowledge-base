# Lifecycle Hooks and Template Access

With `@ViewChild` in `server-element.component.ts` we can use `@ViewChild` in the `server-element.component.html` file to get access to template elements

For example, we placed a local reference named heading on an element and used @ViewChild to access it
`@ViewChild('heading') header: ElementRef;`

Because of lifecycle hooks and timing, we learned the importance of the component's lifecycle hooks
In the video Max attempted to access the heading element in the `ngOnInit` hook, but it resulted in an empty line in the console because the template had not been rendered yet

- To access template elements, we should use the `ngAfterViewInit` lifecycle hook
  - This hook is called after the view has been initialized and the template is ready for interaction
  - In this hook, we successfully accessed and logged the textContent of the heading element, which displayed the expected content

So we learned that using the `ngAfterViewInit` lifecycle hook is crucial when we need to interact with template elements because it ensures that the template has been fully rendered and is ready for manipulation

```
ngAfterViewInit() {
  console.log('ngAfterViewInit called!');
  console.log('Text Content: ' + this.header.nativeElement.textContent);
}
```
