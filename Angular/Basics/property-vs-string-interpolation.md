# Property Binding vs String Interpolation

## String Interpolation

- Use when we want to output something in our template and print some text to it

## Property Interpolation

- Use when we want to change some property like an HTML element, directive, or component

## Don't mis property binding and string interpolation

- Between the quotation marks of property binding we can and must have a typescript expression that will return the value this property expects
  `[disabled]="!allowNewServer"`
  and avoid doing --> `[disabled]="{{!allowNewServer}}"`
  > mixing string interpolation breaks it
