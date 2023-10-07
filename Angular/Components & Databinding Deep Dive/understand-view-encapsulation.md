# Understanding View Encapsulation

- _View encapsulation is a mechanism in Angular that restricts the scope of styles to specific components_
  - **View encapsulation in Angular ensures that styles we write for one component stay contained within that component**
    - Making sure that styles defined for one component don't unintentionally affect other components

For the example, Max talked about how we added a blue text to the paragraph element`<p>` in a component, then we saw in the developer tools that Angular added a attribute like [_ngcontent-ejo-1] to it

- Styles defined with this attribute selector, like `p[_ngcontent-ejo-1] { color: blue; }`, will only target that specific paragraph within our component

- Angular enforces view encapsulation by adding unique attributes to elements in a component's template
  - These attributes, like `[_ngcontent-ejo-1]`, `ejo-0`, `ejo-2`, are automatically attached to elements and are used as selectors for component-specific styles

View encapsulation helps prevent style leakage and conflicts between components

It allows us to write component-specific styles without worrying about affecting other parts of the application

So Basically _Angular emulates the behavior of the shadow DOM, a technology not universally supported by browsers_ and it assigns unique attribute selectors to elements in a component to achieve style encapsulation

**View encapsulation in Angular ensures that component specific styles are applied only to the elements within that component, enhancing the maintainability of our application's styles**
