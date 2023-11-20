# Adding Service Workers

## What are service workers?

- Our JavaScript code traditionally runs in a single thread, but service workers provide an additional thread

- Service workers act as a proxy, managing multiple pages, and handling outgoing network requests

- They are decoupled from HTML pages, enabling them to run in the background and perform advanced tasks

## Add the Angular Service Worker Package

Angular offers a package for easily integrating a service worker into our app, @angular/service-worker

To install this package using the Angular CLI:
`ng add @angular/pwa` to configure our existing project to use the Angular Service Worker Package and start with a pre-configured service worker

- The `app.module.ts` is modified to include the Angular Service Worker module in our `imports: [ServiceWorkerModule.register('/ngsw-worker.js')]`

- The `ngsw-worker.js` file is auto-generated during the build process and contains the service worker logic functionality which we don't have to and typically don't want to write on our own
  - It will be generated during the build process and it will be in the _dist folder_
- The Angular CLI's `angular.json` file is adjusted to enable service worker functionality during the production build

## Testing the Service Worker

Here we install a lightweight node server

- We use a simple node server 'http-server' to host our production app locally for accurate testing:
  `npm install -g http-server`

Then we just run build then change directory and run http-server and assing it a port
First in our project we do: `ng build --configuration=production`
Then we change into the folder directory: `cd dist/project-name`
Finally run: `http-server -p 8081`

Now we should be able to see it in the `localhost:8081`
Then we can observe the service worker in action, caching resources, and managing outgoing requests

Max helps us understand how the service worker allows the app to work offline by caching and serving resources

## Configuring Service Worker Behavior

We customize the behavior of the service worker in the `ngsw-config.json` file

Tailor caching strategies and decide which resources to cache or omit for offline functionality

_We repeat those terminal steps in that order when we make changes to the app and we want to add to the offline page_
