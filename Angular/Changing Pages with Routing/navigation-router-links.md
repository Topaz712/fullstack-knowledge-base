# Navigating with Router Links

**Avoid using plain href links with paths because they cause the page to reload on navigation, reloading the page resets the app, leading to the loss of the entire application state, which is not user-friendly**

Instead, we should use the `routerLink` directive to navigate in our Angular applications

`routerLink` can accept a string `routerLink="/">Home"` or can also be used by property binding `[routerLink]="['/users']"` to define the route

It can also have array of path elements, like doing this `<a [routerLink]="['/users', 'something']">` will make an absolute path, which will be discussed later in the lessons

```
<ul class="nav nav-tabs">
<li role="presentation" class="active"><a routerLink="/">Home</a></li>
<li role="presentation"><a [routerLink]="['/servers']">Servers</a></li>
<li role="presentation"><a [routerLink]="['/users']">Users</a></li>
</ul>
```

- This special directive handles clicks differently, preventing page reloads and preserving the app's state

- Using `routerLink` is more efficient than reloading the page, making it a better choice for navigating within the app
