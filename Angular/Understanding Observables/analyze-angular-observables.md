# Analyzing Angular Observables

In order to follow along smoothly with the course examples of the video segment we have to make sure we install 'RxJS v6' by running:

`npm install --save rxjs@6`

Also, install the `rxjs-compat` package:

`npm install --save rxjs-compat`

- In this video segment of the lesson, we have a simple Angular project with three links leading to different pages and we're focusing on the "user" component, where there's a subscription set up to listen to changing route parameters
  - This subscription will allows us to update the displayed user ID in the DOM as we navigate between different user pages

The core concept here is going to be observables, which are streams of data and when data changes in these streams, our subscriptions will get notified

- In the context of this lesson project, 'params' is the observable
  - It's a data stream that provides new route parameters whenever we go to a different page
  - In the subscription's function, we extract the relevant parameter, which is the user ID in this case

_Angular relies heavily on observables and we typically subscribe to existing observables instead of creating them ourselves_
