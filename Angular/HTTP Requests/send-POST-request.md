# Sending a POST Request

To use Angular's HTTP client, we first need to enable it by adding the HttpClientModule and adding it to our imports array in _app.module.ts_:

```
import { HttpClientModule } from '@angular/common/http';
....
....
imports: [BrowserModule, FormsModule, HttpClientModule],
```

We have a simple project with a form template-driven form that lets us create a new post and store it on Firebase

We inject the HttpClient into our _app.component.ts_ by creating a property named http

Then create the _onCreatePost method_ to handle sending an HTTP request, and this method takes _post data_ in a specific format

- In the _onCreatePost method_, we use the `this.http.post method` to send a _POST_ request to a specific URL, which is usually a Firebase database Url

- The post method requires a Url and request data, we use our post data as the request data
  - Normally, we send JSON data in RESTful APIs, Angular automatically transforms our JavaScript object into JSON, this setup ensures that the request has the right Url and data, and we don't need to add more data/details

In _app.component.ts_:

```
import { HttpClient } from '@angular/common/http';
....
constructor(private http: HttpClient) {}
....
  onCreatePost(postData: { title: string; content: string }) {
    // Send Http request
    this.http.post(
      'https://http-requests-code-along-default-rtdb.firebaseio.com/posts.json', postData
      ).subscribe(responseData => {
        console.log(responseData);
      });
  }
```

The request is only sent when we subscribe to the observable returned by `http.post`

- When we subscribe, we can access the response data within the subscribe block

We note that HTTP requests are managed through observables, and requests are only sent when we subscribe to them

When we send the request, we notice two network requests in the browser, the first one of type "options" checks if the post request is allowed and if successful, it sends the actual post request, the JSON data is sent in the request payload

So in this video we've set up our Angular application to send a POST request to store data in a Firebase database, requests are managed as observables, and Angular's HTTP client takes care of data transformation and communication with the server
