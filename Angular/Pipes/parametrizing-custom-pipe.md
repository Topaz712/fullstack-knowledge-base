# Parametrizing a Custom Pipe

In our _app.component.html_, the parameters for a custom pipe can be defined using a colon `:` like so:

`<strong>{{ server.name | shorten:15 }}</strong>`

We can enhance our custom pipe class _ShortenPipe_ to allow us to specify the character limit

To do this we modify the transform method to accept a second argument, like _limit_ which should be of type number
In _shorten.pipe.ts_:

```
export class ShortenPipe implements PipeTransform {
  transform(value: any, limit: number) {
    if (value.length > limit) {
      return value.substr(0, limit) + ' ...';
    }
    return value;
  }
}
```

We use this parameter to determine when to shorten the value

Additional parameters can be added by including extra arguments in the transform method and specifying them in the template using colons `:` like so:

typescript would be:
`transform(value: any, limit: number, anotherArg: any)`
html would be:
`<strong>{{ server.name | shorten:15:secondArg }}</strong>`

So basically with this change adjustment, it lets us customize the behavior of our custom pipe by passing parameters, making it flexible and compatible with built in Angular pipes
