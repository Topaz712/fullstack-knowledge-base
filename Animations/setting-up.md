# Setting Up A Starting Project

The Animation functions were moved into their own package, now also need to be added as a special module to our imports[] array in the AppModule

If we don't already have it installed: `npm install --save @angular/animations`

Add the `BrowserAnimationsModule` to our _imports[] array in AppModule_ and needs to be _imported from @angular/platform-browser/animations'_ so:
`import { BrowserAnimationsModule } from '@angular/platform-browser/animations';`

Then we can import trigger , state , style etc from @angular/animations instead of @angular/core
