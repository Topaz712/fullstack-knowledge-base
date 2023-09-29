# Styling Elements Dynamically with ngStyle

`ngStyle` is a built-in directive which we can configuration to do something, we can use property binding on this directive

By adding square brackets to our `[ngStyle]` we indicate we want to bind a property on this directive and it just happens for the example it is also called ngStyle

Can be use as so:
`<p [ngStyle]="{backgroundColor: isColor ? 'blue' : 'green' }">`
`[ngStyle]="backgroundColor: 'blue'"`

## Keep in mind Property Binding and Directive Binding are not the same! They're totally different

So it's gives our website the ability to transform its style dynamically
