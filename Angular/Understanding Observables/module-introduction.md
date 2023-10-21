# Module Introduction

## What is an observable?

- An observable can be thought of as a data source
  - In Angular, an observable is an object imported from the rxjs library, which is implemented following the observable pattern
  - It operates as a data source that emits events or data packages over time, depending on the data source, these data packages are emitted on a timeline or stream

### There are two main parts to an observable

- _The Observable_ - It's the source of data packages, like user events, HTTP responses, and more

- _The Observer_ - It represents our code and it's where we subscribe to the observable to receive data packages

### Observables emit data packages in response to events

- These data packages fall into three categories

  - Normal Data
    - It's the typical data packages we expect
  - Errors
    - If an error occurs, the observable emits an error
  - Completion
    - When the observable has no more data to emit, it completes

We will use these data categories to execute your code as needed

### Observables may or may not complete

- Some observables, like user events, never really complete because they depend on user actions

- Other Observables, like HTTP requests, have a clear endpoint when they complete

### Observables are used to handle asynchronous tasks

- Asynchronous tasks are those that we don't want to block our program with, because we don't want to wait for user interactions or long-running HTTP requests since we don't know when they will happen and we don't know how long they will take

- Historically, callbacks and promises were used for this purpose, but observables are an alternative approach of handling

### Angular makes extensive use of observables

- Angular uses observables to efficiently manage asynchronous tasks

So basically, we need to understand that observables are essential for working with Angular, since we'll frequently encounter them in the framework
