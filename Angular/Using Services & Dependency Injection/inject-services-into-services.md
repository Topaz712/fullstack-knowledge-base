# Injecting Services into Services

- By adding a service to the providers array in the `app.module.ts`, we're making sure that the whole application shares the same instance of that service

  - This allows us to inject the service into other services, making our more code organized and modular

- To enable service injection, we need to provide the service in the app module using the providers array

- A service should have the `@Injectable()` decorator attached to it to indicate that it can receive injected dependencies

- We don't need to add a `@Injectable` decorator to a service if we're not injecting anything into it

In the newer Angular, it's recommended to add `@Injectable` to all services for future compatibility, even if it's not strictly required in the current Angular version that Max has in these video sections

We don't add `@Injectable` to the service we're injecting but to the service where we want to perform the injection "the receiving service"
