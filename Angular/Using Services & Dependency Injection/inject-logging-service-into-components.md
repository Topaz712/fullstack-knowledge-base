# Injecting the Logging Service into Components

- Services in Angular are TypeScript classes used to centralize and manage code

- Angular provides a more efficient way to create services, avoiding manual imports

- Angular's Dependency Injector is a tool that manages and injects service instances into components

- Components can inform Angular about their service dependencies by adding a constructor

  - The constructor parameter specifies the required service like so: `constructor(private loggingService: LoggingService)`

- Angular recognizes this and attempts to provide an instance of the required service

  - The service instance is automatically created and injected into the component
  - But to enable this, the component must specify the service type in the constructor and import the service `import { LoggingService } from '../logging.service';`

- The component also needs to inform Angular about how to create the service using the providers property in the component decorator

```
@Component({
  selector: 'app-account',
  templateUrl: './account.component.html',
  styleUrls: ['./account.component.css'],
  providers: [LoggingService] //right hereeeeeee
})
```

With the service injected, components can use it to access and utilize its functionality
`this.loggingService.logStatusChange(accountStatus);`
By using services, you can centralize functionality, eliminate duplicate code, and create more maintainable and efficient applications
Make sure to have `D.R.Y`-`Dont Repeat Yourself` code!

```
export class NewAccountComponent {
  @Output() accountAdded = new EventEmitter<{name: string, status: string}>();

  constructor(private loggingService: LoggingService){}

  onCreateAccount(accountName: string, accountStatus: string) {
    this.accountAdded.emit({
    name: accountName,
    status: accountStatus});

    this.loggingService.logStatusChange(accountStatus);
  }
}
```
