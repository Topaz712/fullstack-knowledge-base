# Redirecting and Wildcard Routes

If users were to enter a URL path that doesn't exist in our application, we want to provide proper error handling and redirect them to a "404 Not Found" page

To handle unknown routes, we have to set up redirection and wildcard routes in our application

- By using redirection and wildcard routes, we are ensuring that our application handles unknown or invalid paths efficiently, improving the user experience and providing clear error messages

First we create a page-not-found component with the Angular ClI then in the `page-not-found.component.html` we write our message to serve as our 404 error page like:
`<h3>This page is not found!</h3>`

Next we define a route that matches the _not-found path_ in our `app.module.ts`:

```
{ path: 'not-found', component: PageNotFoundComponent },
{ path: '**', redirectTo: '/not-found'}
```

To handle any unknown routes, we create a wildcard route using the _double asterik route_ `**` and specify that it redirects to the _not-found_ route

- Now when a user enters an invalid URL or an unrecognized/nonexistant path, they will be automatically redirected to the _PageNotFoundComponent_ which displays the _"404 Not Found"_ message

## Remember the order of routes is important! Ensure that the wildcard route is the last one in our route configuration because our routes get passed from top to bottom, so if the generic route was at the beginning we would always get redirected
