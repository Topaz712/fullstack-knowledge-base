# Observing Different Types of Responses

In this part of the lesson, we learned how to work with the entire HTTP response object, not just the response body

Sometimes we need access to more information than just the response body, like the status code or response headers so we would need _access to the full response_

We can change the way Angular's HTTP client processes the response by modifying the observe parameter in our Http request by _modifying the observation_

In _posts.service.ts_:

```
createAndStorePost(title: string, content: string) {
    const postData: Post = {title: title, content: content};
    this.http
    .post<{ name: string }>(
      'https://http.........../posts.json',
      postData,
      {
        observe: 'response'
      }
      ).subscribe({
        next: (responseData) => {
        console.log(responseData);
      }, error: (error) => {
        this.error.next(error.message);
      }
      });
  }
```

The default value for _observe is 'body'_ which automatically extracts and converts the response data to a JavaScript object

So by setting _observe to 'response'_ we get the full HTTP response object, including the response body

- Another option is to set _observe to 'events'_ which gives us more granular control over the request lifecycle and different types of events

- We can use the _tap operator_ to perform actions without altering the response data, it allows us to inspect the events

- Events come in different types, represented by numbers

We can use a *TypeScript only feature HTTPEventType enum*for more human readable event type comparisons in our log

- Examples of events include 'Sent' 'Response' and like 'UploadProgress' to get back some progress information when working with file uploads to see how its going
  - We can use these events to customize the behavior of our app based on the request phase

_Events are handy when we need fine grained control over our request data and UI updates based on the request phase_

- If we ever need to check whether we received a response in our Http request, we can compare the event type to see if it's a response event
  - If it is, we can safely access the response body, but if the event type is something else, like 'sent' then we can perform different actions based on that event type

```
 deletePosts() {
    return this.http.delete(
      'https://http............./posts.json',
      {
        observe: 'events'
      }
    )
    .pipe(
      tap(event => {
        console.log(event);
        if (event.type === HttpEventType.Sent) {
          // ...
        }
        if (event.type === HttpEventType.Response) {
          console.log(event.body);
        }
      })
      );
  }
```

- We log the event to see what type of event we're dealing with
  - If the event type is 'Sent' we can execute specific actions related to the sending phase
  - If the event type is 'Response' we can log or work with the response body

This allows us to respond differently based on the phase of the HTTP request, like sending or receiving data

By working the full response object and events, we can adapt our application to various scenarios and requirements, ensuring we have all the information we need to handle different aspects of our Http requests
