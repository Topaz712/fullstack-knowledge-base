# Understanding the Different Approaches

- From what we have learned of dynamic components, we've focused on the concept of showing components dynamically when needed, meaning they're not always present but appear based on specific code conditions
  - The current method we're using is `*ngIf` a declarative approach where we add the component selector in our template and use `*ngIf` to load it conditionally
    - A method where we put the component in our template and use `*ngIf` to decide when it should appear, it efficiently controls whether the DOM includes that component

`*ngIf` is a great choice for dynamic component loading, saving us from extra steps that other methods would require

Currently in our project we're using `*ngIf` in our project, especially for features like the alert box

- In the past, there was the Dynamic Component Loader, but it's no longer recommended

  - Instead, we create a component in our code and manually attach it to the DOM/webpage
    - With this approach, we take control of how the component is instantiated, how data is passed to it, and how it's removed, things `*ngIf` normally handles for us

In _auth.component.html_

```
<ng-template appPlaceholder></ng-template>

<div class="row">
  <div class="col-xs-12 col-md-6 col-md-offset-3">
  <div *ngIf="isLoading" style="text-align: center;">
    <app-loading-spinner></app-loading-spinner>
  </div>
```

In _auth.component.ts_

```
Import { PlaceHolderDirective } from '../shared/placeholder/placeholder.directive';

@Component({
  selector: 'app-auth',
  templateUrl: './auth.component.html'
})

export class AuthComponent {
  isLoginMode = true;
  isLoading = false;
  error: string = null;
  @ViewChild(PlaceholderDirective, {static: false})
```

- Instead of passing a string of a local reference in ViewChild, we also can pass a type and it will look for hte existence of that type in the template

  - So if we pass the placeholder directive in the template, as a type, it will automatically find the first place where we used that directive in the template of this component

- This alternative can be beneficial when we need full control from our code and prefer not to manipulate the template
  - Sometimes, adding a component to the template might not be practical, making this approach interesting
