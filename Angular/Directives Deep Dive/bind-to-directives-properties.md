# Binding to Directive Properties

We will introduce the concept of custom property binding in directives, which allows us to pass data from the component using the directive to customize its behavior

- For this we add two new properties to our directive using the `@Input` decorator: defaultColor and highlightColor
  - These properties can be set from the outside

```
@Input() defaultColor: string = 'transparent';
@Input('appBetterHighlight') highlightColor: string = 'blue';
@HostBinding('style.backgroundColor') backgroundColor: string = 'transparent';
```

By providing default values for these properties, we ensure that our directive works even if no values are explicitly set

We learned that when using custom property binding, we can bind to properties of our own directives by placing them on the same element, enclosed in square brackets

We also saw how to set an alias for our directive property using the `@Input` decorator's alias feature, making it more user-friendly when binding.

It was mentioned that if we pass a string as a value for property binding, we can skip the square brackets and single quotation marks, but it's essential, to ensure clarity

`<p [appBetterHighlight]="'red'" defaultColor="yellow">Style me with better directive!</p>`

Finally, we saw that by dynamically setting the values of defaultColor and highlightColor from the component, we can change the directive's behavior, allowing for customization based on application logic or user preferences

In the code of Max's video, we bound the `[appBetterHighlight]` directive to change colors dynamically, showing the power of custom property binding in creating more versatile and user-friendly directives

In this lesson, we enhanced our directive's functionality to allow dynamic customization of colors based on user or application preferences
