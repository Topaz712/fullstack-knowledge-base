# Getting Access to ng-content with @ContentChild

To access projected content in our `app.component,html` we added a reference on the projected paragraph `<p #contentParagraph` because we want to project it into our `server-element.component.ts`

Then we decide where to use `@ViewChild` or `@ContentChild`

- Initially, we considered using `@ViewChild`, but it wouldn't work because the projected content is not part of the view of the app component

- So the better choice is going to be `@ContentChild` , we learned it's a decorator that allows us to access content that is projected into a component through `<ng-content>`
- So we used `@ContentChild` by specifying the selector "contentParagraph" and storing it in a property of type ElementRef like so : `@ContentChild('contentParagraph') paragraph: ElementRef;`

We learn that just like with `@ViewChild` we can't access the content before reaching the `ngAfterContentInit` lifecycle hook

- We learned that by accessing and logging the `textContent` of the projected paragraph in the `ngAfterContentInit` hook

So basically we learned how to use `@ContentChild` to access and work with content that is projected into a component using `<ng-content>` and it's pretty useful when you need to interact with content from other components that is passed through `<ng-content>`
