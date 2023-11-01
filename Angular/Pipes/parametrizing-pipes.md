# Parametrizing Pipes

We can customize the behavior of pipes by passing parameters

- Like for the _date pipe_ we pass the _parameter 'fullDate'_ to format a date differently

  - A colon `:` is used to pass parameters to pipes
  - It's a powerful way to customize how pipes transform our data for our specific needs

- Max also mentions that pipes need to be able to handle parameters, and different pipes might have different parameter options
  - He also noted that we can separate multiple parameters with additional colons if needed `words:'Hello':'There'`

In app.component.html:
`{{ server.started | date:'fullDate' }}`

On application it looks like this:

BEFORE:

```
Production Server | MEDIUM | Aug 8, 1920
User Database | LARGE | Aug 8, 1920
```

AFTER:

```
Production Server | MEDIUM | Sunday, August 8, 1920
User Database | LARGE | Sunday, August 8, 1920
```
