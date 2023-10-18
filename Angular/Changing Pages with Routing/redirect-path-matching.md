# Redirection Path Matching

In the video where Max taught us how to redirect wildcard routes, we didn't encounter any issues when we tried to redirect the user, however that's not always the case when adding redirections

By default, Angular matches paths by prefix, meaning a route like `{ path: '', redirectTo: '/somewhere-else' }` will match both `/recipes` and `/`

The default prefix matching strategy is 'prefix' which can lead to unexpected behavior

The route will _ALWAYS_ redirect us to _'/somewhere-else'_ because every path starts with parenthesis `''` **which is not a whitespace, just "nothing"**

To fix this behavior of constant redirecting, we change the matching strategy to **full** using `pathMatch: 'full'` like:

`{ path: '', redirectTo: '/somewhere-else', pathMatch: 'full' }`

This ensures we only get redirected when the full path is `''` _only if there is no other content in our path_

Using the 'full' path matching strategy, let's us control when redirection occurs and avoid unintended redirects in the app
