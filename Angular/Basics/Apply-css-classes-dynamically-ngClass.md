# Applying CSS Classes Dynamically with ngClass

Where _ngStyle allowed us to change the CSS style itself_, **ngClass allows us to dynamically add or remove CSS classes**

`ngClass` only works as intended when using property binding

## Key value pairs

- The keys are the CSS clas names
- The values are the conditions determining whether the class should be attached/added or not

```
<p
[ngStyle] = "{ backgroundColor: getColor() }"
[ngClass] = "{ online: serverStatus === 'online' }">
{{ 'Server' }} with ID {{ serverId }} is {{ getServerStatus() }}
</p>
```

They way ngClass works is it only adds a CSS class if a certain condition is true.
