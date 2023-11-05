# Using Types with the HttpClient

Now that we're focusing on outputting our posts, we address a minor issue and thats when we hover over posts, we notice it's of type `'any'`, so this means TypeScript can't grasp the format of our posts because it only sees the _id:key_

To make it more understandable, we can assign a type since we enhance our code's clarity and maintainability by assigning types to our data

First we create a new file `'post.model.ts'` and we define an interface called 'Post', specifying the 'title' 'content' and an optional 'id' by adding a question mark

In _post.model.ts_:

```
export interface Post {
  title: string;
  content: string;
  id?: string;
}
```

With this interface defined, we can now use 'post' as our type in _app.component.ts_:

```
import { Post } from './post.model';
....
private fetchPosts() {
    this.http
    .get<{ [key: string]: Post }>('https://http-requests-code-along-default-rtdb.firebaseio.com/posts.json')
    .pipe(
      map(responseData => {
        const postsArray: Post[] = [];
        for (const key in responseData) {
          if (responseData.hasOwnProperty(key)) {
            postsArray.push({ ...responseData[key], id: key })
          }
        }
        return postsArray;
      })
      )
      .subscribe(posts => {
        // ...
        console.log(posts);
      });
  }
```

In the 'fetchPosts' method, we use the Angular HTTP client's generic method on 'GET' because it lets us specify the expected response body type within angle brackets

By doing this, we clearly communicated that our response data will match the _'Post' interface's format_

This type specification enhances our code by providing improved auto completion and in helping prevent TypeScript errors

It's an optional but highly recommended practice to ensure code quality
