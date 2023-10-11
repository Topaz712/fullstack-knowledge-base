# Understanding the Hierarchical Injector

- Angular's dependency injector is hierarchical, so that means it manages the availability of services across different levels in the app

- When a service is provided in a component, that component and all its child components "and their children", receive the same instance of the service

- At the highest level, the appModule can provide a service, making that instance available throughout the entire application

- Services can also be injected into other services, to make our code more organized and modular

- The scope of a service's instance is limited to the component and any child components it has, but not the parent components or its siblings

- Instances of a service don't propogate upward to parent components, they only move downward to child components
  - So if you provide a service in a component with no child components, that component will have its own instance of the service
  - This instance won't be accessible to any child components it doesn't have, and it will even overwrite any higher-level instances of the service.
    - If a service is provided at a lower level, it will override the same service provided at a higher level

## In a hierarchical structure:

- App Module: Service instance available application-wide

- App Component: Service instance available for all components "except other services"

- Any Other Component: Service instance available for the component and all its child components.

This hierarchy allows for efficient and organized service management in Angular applications
