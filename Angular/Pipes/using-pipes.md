# Using Pipes

- By adding pipes to the template, we transform the way data is displayed to users without changing the actual data itself
  - Pipes provide a convenient way to enhance the presentation of data in Angular applications

We used the uppercase pipe for `server.instanceType`, this pipe converted the instance types to uppercase

We used the date pipe for `server.started`, this pipe formatted the date into a more readable format

In _app.component.html_:

```
<strong>{{ server.name }}</strong> |
{{ server.instanceType | uppercase }} |
{{ server.started | date }}
```

On application it looked like this:

BEFORE:

```
Production Server | medium | Mon Aug 8 1920 00:00:00 GMT+0200(CEST)
User Database | large | Mon Aug 8 1920 00:00:00 GMT+0200(CEST)
```

AFTER:

```
Production Server | MEDIUM | Aug 8, 1920
User Database | LARGE | Aug 8, 1920
```
