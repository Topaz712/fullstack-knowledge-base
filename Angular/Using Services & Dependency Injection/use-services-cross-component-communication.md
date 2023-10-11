# Using Services for Cross-Component Communication

This video lesson Max explains the use of services for cross-component communication

- Normally, without services, we'd have to emit events and manage complex chains of property and event bindings to communicate between components
- Even so, services offer a simpler way to achieve this
  - We can use services to provide events that can be triggered in one component and listened to in another
  - This approach can save us a lot of coding effort
  - The key things to remember are that services are valuable for cross-component communication and can make our code more efficient and also, ensures we have the right number of service instances and, when injecting services into other services, we must provide the service at the app module `app.module.ts` level and use the `@Injectable` decorator appropriately
