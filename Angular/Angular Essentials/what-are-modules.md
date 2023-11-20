# What are Modules?

- Angular modules serve as bundles/containers for organizing different elements like components, directives, services, and pipes in Angular applications
  - Unlike regular JavaScript modules, Angular modules are specific to Angular and are necessary for Angular to understand and manage the application's features

_AppModule_ - Angular analyzes NgModules to "understand" our application and its features

_AppComponent_ - Angular modules define all building blocks our app uses like Components, Directives, Services

_ProductsComponent_ - An app requires at least one module (AppModule) but may be split into multiple modules

_Highlight Directive_ - Core Angular features are included in Angular modules _like FormsModule_ to load them only when needed

_ProductsService_ - We can't use a feature/ building block without including it in a module

- In Angular, we have to explicitly define and group components and services into modules since Angular doesn't automatically detect them
  - Every Angular app must have at least one module, also known as the app module, but we have the option of splitting it into multiple, smaller, and more manageable modules

Additionally, Angular itself provides core features organized into modules, like the Forms module, this modular structure simplifies development by offering specialized modules like Forms, which contain various directives related to forms

_Importantly, we can't use a specific feature or building block in Angular without including it in a module_ The process of inclusion, whether through Declarations or Providers, depends on the particular feature being used

Understanding and effectively utilizing Angular modules is fundamental for creating well organized Angular applications
