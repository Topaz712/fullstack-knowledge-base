# Styling Active Router Links

- Active router links help to visually represent active routes through CSS classes

- The `routerLinkActive` directive allows us to dynamically set a class for active links

  - Although we can add `routerLinkActive` to the wrapping element like the list item `<li> `or the link `<a>` itself but adding it to the link itself wouldn't do anything when using bootstrap so for adding the visual to the tabs we need to add it to the list element

- The directive checks the currently loaded path and marks the active class on links that match this path

By default, it considers a link active if it's part of the loaded path, which may not always be what we want so to ensure exact matching for the full path, we can add `routerLinkActiveOptions` with exact: true:
`[routerLinkActiveOptions]="{exact: true}"`

```
      <ul class="nav nav-tabs">
        <li role="presentation"
        routerLinkActive="active"
        [routerLinkActiveOptions]="{exact: true}">
        <a routerLink="/">Home</a>
      </li>
```

This configuration ensures that the active class is applied only if the link matches the full path, not just a part of it
