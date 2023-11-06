# Outputting Posts

Now that we've fetched our data, it's time to display it in our application and instead of just logging it, we transform it into an array of posts

In _app.component.ts_:

```
 loadedPosts: Post[] = [];
 ....
private fetchPosts() {
....
....
)
  .subscribe(posts => {
    // ...
    this.loadedPosts = posts;
  });
}
```

- We created a property called _loadedPosts_ and we explicitly set its type to an array of posts `loadedPosts: Post[] = [];`

  - Then in our _fetchPosts method_ we subscribe to the fetched data and assign it to loadedPosts

- Now in our _app.component.html_ we want to show the posts only if we have them, so we use an \*_ngIf directive_ to check if the length of loadedPosts is less than one `<p *ngIf="loadedPosts.length < 1">`, indicating no posts
  - If we have posts, we create an unordered list with Bootstrap styling and use \*_ngFor to iterate through loadedPosts_, showing the title and content of each post
  - If there are no posts, we display a message

In _app.component.html_:

```
<p *ngIf="loadedPosts.length < 1">No posts available!</p>
      <ul class="list-group" *ngIf="loadedPosts.length >= 1">
        <li class="list-group-item" *ngFor="let post of loadedPosts">
          <h3>{{ post.title }}</h3>
          <p>{{ post.content }}</p>
        </li>
      </ul>

```

This process allows us to transition from fetching data to effectively displaying it in our frontend
