# Editing the First App Video

In this video he went over briefly on how using ngModel and importing FormsModule to html and ts make our browser page

ngModel keeps our UserInterface and code in sync for user input
FormsModule helps you build and check forms easily in Angular.

## ngModel:

- Helps connect what users type in input fields with your code.
- If a user types something, our code knows about it instantly.
- Example: `<input type="text" [(ngModel)]="name">` links input to a name variable. `<p>{{name}}</p>`

## FormsModule:

- You need to import it to use these tools in your app.
  > In the app.module.ts file we would do `import { FormsModule } from '@angular/forms';` then under it on the `@NgModule` in the imports: add `FormsModule`
- Makes handling forms like sign-up or login easier it seems
- Provides tools to check if fields are filled correctly. Like in the video when we type in the input field, the text under it also changes to what we're typing
- Helps manage user input effectively.
