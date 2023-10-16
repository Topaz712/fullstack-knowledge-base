# Passing Parameters to Routes

- In our Angular application we will define routes in the `app.module.ts` using the `const appRoutes : Routes` array

for our users.component.ts

```
export class UsersComponent {
  users = [
    {
      id: 1,
      name: 'Max'
    },
    {
      id: 2,
      name: 'Anna'
    },
    {
      id: 3,
      name: 'Chris'
    }
  ];
}

```

- So to create dynamic routes in our `app.module.ts` file, we can include parameters by adding a colon, like `:id`, within our route path

```
const appRoutes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UsersComponent },
  { path: 'users/:id', component: UserComponent },
  { path: 'servers', component: ServersComponent },
];
```

So if we wanted to load a specific user data for the UsersComponent, we would define a route like `{ path: 'users/:id', component: UserComponent },`

- The colon for `:id` indicates that this part of the path is dynamic, and can be replaced by any value, so Angular will load the UserComponent and allow us to access the dynamic id parameter

  - It needs to have a colon otherwise if we only did `users/id` then for ID literally the words with ID would load instead

- When a user accesses a route like `localhost:4200/users/1`, Angular recognizes 1 as the id parameter
  - We can then retrieve and use this parameter's value within the loaded UserComponent

This method enables us to pass and access data dynamically in our routes, making our application more flexible and interactive
