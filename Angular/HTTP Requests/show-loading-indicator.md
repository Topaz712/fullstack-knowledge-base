# Showing a Loading Indicator

We're making our app more user-friendly by adding a loading indicator so we use a property called _isFetching which is initially false_
Then when we _start fetching posts_, we set _isFetching to true_ and _after fetching it's set back to false_

In _app.component.ts_:

```
export class AppComponent implements OnInit {
  isFetching = false;
.....
 private fetchPosts() {
    this.isFetching = true;
  .....
    .subscribe(posts => {
        this.isFetching = false;
        this.loadedPosts = posts;
      });
  }
}
```

Then in _app.component.html_:

```
<p *ngIf="loadedPosts.length < 1 && !isFetching">No posts available!</p>
<ul class="list-group" *ngIf="loadedPosts.length >= 1 && !isFetching">
  <li class="list-group-item" *ngFor="let post of loadedPosts">
          <h3>{{ post.title }}</h3>
          <p>{{ post.content }}</p>
        </li>
      </ul>
      <p *ngIf="isFetching">Loading...</p>
    </div>

```

- We control what we show in the template by adding an `*ngIf directive` and if we have no posts and aren't fetching, we display _"No posts available"_
  - When fetching, we show a loading message
  - If we have posts and aren't fetching, we display them

This way, we ensure a better user experience with a loading indicator, which works even if the server is slow
