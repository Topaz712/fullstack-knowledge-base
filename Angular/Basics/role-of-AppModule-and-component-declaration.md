# Understanding the Role of AppModule and Component Declaration

Angular uses components to build web pages & uses modules to bundle different pieces/components of our app into packages

- In the `app.module.ts` file , it will contain what is needed to give the Angular application its
  functionality, we need to tell it because simply creating the file isn't enough.
  > **New components need to be registered in the `declarations` array**

As a reference this is not Angular, it is a TypeScript feature, so by doing this, TypeScript knows where to find the component therefore everything can be bundled and now when Angular runs, it will know about the server `component`.
