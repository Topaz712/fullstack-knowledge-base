# Working with Component Styles

We can style or css for the html file in the css file or in the components.ts file which references style sheets

`StyleUrl:` is an array because we can reference multiple external stylesheets if we wanted to and we can also just use `styles:` , it has to be either one or the other not both, and with just having `styles:` it also takes an array but with strings, for example:

```
styles: [`
  h3 {
    color: dodgerblue;
  }`]
```

> use backticks when using multiline code

Same applies with templates, if we can more code in there, then an external file is a good idea and if its a short definition we can just keep it in the typescript file
