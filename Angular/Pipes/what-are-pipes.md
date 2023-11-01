# Introduction & Why Pipes are Useful

- Pipes in Angular 2 are tools that transform data output in templates

- They work with various types of data, including synchronous and asynchronous

Like if we want to display a username in uppercase without altering the actual property, we can achieve this using a built-in pipe, like the uppercase pipe :

```
username = 'Topaz'

<p>{{ username }}</p>

Topaz

<p>{{ username | uppercase }}</p>

TOPAZ
```

**The primary goal of pipes is to transform output data, making them a handy feature in Angular**
