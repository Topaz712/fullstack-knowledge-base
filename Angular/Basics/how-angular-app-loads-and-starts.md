# How an Angular App gets Loaded and Started

Angular is a framework that allows us to create single page applications

- The single page that gets served is in the index.html
- Components tie in our applications in the end

- Whenever the ng process rebuilds our project, it will create javscript script bundles and automatically add the right imports in the index.html file
- So in the final index.html file, these scripts gets served in the browser
  > these scripts imports are presents and these script imports will contain our own code too.
  > these script files in the main.ts file are the first code to be executed

In the `main.ts` file, bootstrap stars our Angular application by passing an app module to this method and app module refers to the file `app.module.ts`
Then in `@NgModule` inside the `app.module.ts` file, we get the bootstrap array `bootstrap: [AppComponent]` which lists all the components that should be known to Angular at the point in time it analyzes our `index.html` file

- So Angular gets started, then the `main.ts` files starts and there we bootstrap an Angular application where we pass this module as an argument
  > in there, the module, lets Angular know about the `app.component` when it starts itself

## So basically When the browser encounters an Angular app's script tag, it starts loading the necessary JavaScript files then Angular is initialized and bootstrapped when the JavaScript files are loaded
