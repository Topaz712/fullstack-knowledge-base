# GETting Data

We use the _POST method_ to send requests when we subscribe to them

Now, we want to retrieve all the posts we've stored so to do this, we make a private property called _fetchPosts_ and use of the _GET method_, this method sends a GET request to the same URL used for data storage

- Firebase generates a unique key for each post, and we aim to fetch all posts

We subscribe to this GET request and expect to receive our posts as a JavaScript object in our console, complete with a unique identifier and the original data we stored

In _app.component.ts_:

```
ngOnInit() {
    this.fetchPosts();
  }//created third
....
 onFetchPosts() {
    // Send Http request
    this.fetchPosts();
  }//created second
....
private fetchPosts() {
    this.http
    .get('https://http-requests-code-along-default-rtdb.firebaseio.com/posts.json')
    .subscribe(posts => {
      console.log(posts);
    });
  }//created first
```

To display them in a list, we'll need to convert this object into an array, and we may use observable operators for such transformations

So in our _app.component.ts_, we _call the fetchPosts method in the ngOnInit lifecycle hook to fetch data upon app initialization_

We also provided an _onFetchPosts method_ that also triggers the fetchPosts function, letting us retrieve data in response to user actions

The _fetchPosts method_ sends a _GET request_ to the Firebase Url and logs the data it receives
