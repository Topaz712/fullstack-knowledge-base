# Understanding Angular Error Messages

- When something on our webpage isn't working as expected then we can open up the developer tools and we'll see we've gotten an error message.

- Error messages have gotten better in Angular so there's a chance the error message will be helpful

- It should be at the top, in this case it shows what is causing the problem and it says:

```
EXCEPTION:
Error in ./AppComponent class
AppComponent - inline template:4:6
caused by: Cannot read a property 'push' of undefined
```

So the problem is that in thhe inline template error message it indicates the problem is on "line 4" and "column 6."

- The error message references line 4 because during the build process, all code is merged and rebuilt causing it to trigger on line 4 in the final code so it's not necessarily the problematic code in our template or TypeScript file

- The error message provides us with an important clue: "property push of undefined."

  - This tells us that we're trying to call the push method an object that is not defined at that point in the code

- We see that the code shows that the push method is called in the `onAddServer()` method in the `app.component.ts` file

  - Since the error occurred when clicking a button, it is likely that the issue is within the method that gets executed when the button is clicked.

- The problem is likely related to the line `servers; onAddServer() { this.servers.push('Another Server'); }` in the `app.component.ts` file. so by investigating this line, we see that the variable `servers;` is declared but not defined, leading to it being undefined.
  - To fix this, we need to initialize `servers` as an empty array before attempting to push values into it like so : `servers = [];`

```
export class AppComponent {
  servers; "will turn into --->" servers = [];
  onAddServer(){
    this.servers.push('Another Server');
    }
}
```

**So we learn that understanding error messages is crucial when debugging Angular applications**

## We need to carefully examine error messages, follow file references, and consider specific error descriptions to pinpoint and resolve issues effectively
