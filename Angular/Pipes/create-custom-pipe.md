# Creating a Custom Pipe

- So first we create a new file in our app folder `shorten.pipe.ts`

  - In this file, we define a class for our custom pipe like `ShortenPipe` and _implement the PipeTransform interface_
  - The transform method is important

- Remember that the transform method must always return something because pipes work by taking an input and producing an output

In the transform method, we define how we want to transform the input data so in this case, it will shorten the input to a specified length:

In _shorten.pipe.ts_:

```
import { Pipe, PipeTransform } from "@angular/core";

@Pipe({
  name: 'shorten'
})
export class ShortenPipe implements PipeTransform {
  transform(value: any) {
    if (value.length > 10) {
      return value.substr(0, 10) + ' ...';
    }
    return value;
  }
}
```

**substr(0, 10) means substring and is a built-in method JavaScript offers, Where we can Define how long this string, the substring we want to extract, should be of index 0 and is 10 characters long**

To further improve our custom pipe like checking the length of the input data and adding dots/periods for a prettier output we added the `' ...'`

Then we must import our pipe in the _app.module.ts_ and add it to the declarations array:

```
import { ShortenPipe } from './shorten.pipe';

@NgModule({
  declarations: [
    AppComponent,
    ShortenPipe
```

In our _app.component.html_ template, we apply the custom pipe to the data we want to transform using the pipe symbol `|` :
`<strong>{{ server.name | shorten }}</strong>`

This will all then let us make and use custom pipes that suit our needs

On application it looks like this:
BEFORE:

```
Production Server | MEDIUM | Sunday, August 8, 1920
User Database | LARGE | Sunday, August 8, 1920
```

AFTER:

```
Production ... | MEDIUM | Sunday, August 8, 1920
User Datab ... | LARGE | Sunday, August 8, 1920
```
