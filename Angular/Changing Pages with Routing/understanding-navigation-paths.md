# Understanding Navigation Paths

- Navigation paths in Angular can be either relative or absolute

- A path with a slash `/` at the beginning is an absolute path, and it is appended to the root domain
  - A path without a slash or with a dot `./` is a relative path and gets added to the current path based on the component we are on
    - The current path depends on the component we are currently using
  * Relative paths with `../` allow us to move up levels in the path hierarchy
  * Relative paths inside active components are useful for nested routes

It's important to understand navigation paths so we're able to correctly navigate within our Angular application
