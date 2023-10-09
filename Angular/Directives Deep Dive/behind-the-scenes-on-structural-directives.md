# What Happens behind the Scenes on Structural Directives

Understanding the transformation that occurs behind the scenes when using the asterisk notation provides insight into how Angular handles structural directives, making it easier to work with them effectively

- Structural directives are a special type of directive in Angular used for modifying the structure of the DOM, like adding or removing elements conditionally

- The asterisk `*` before a structural directive like `*ngFor` or `ngIf` is a shorthand notation that makes the code more readable and intuitive

  - I believe i've also heard it be referenced it being essentially a syntactic sugar

- Behind the scenes, Angular changes these asterik structural directives into a longer, detailed format
  - For example, `*ngIf` gets transformed into an `<ng-template>` element with property binding on the ngIf attribute

```
<ng-template [ngIf]="!onlyOdd">
<div>
<li
class="list-group-item"
[ngClass]="{odd: even % 2 !== 0}"
[ngStyle]="{backgroundColor: even % 2 !== 0 ? 'yellow' : 'transparent'}"
\*ngFor="let evenNumber of evenNumbers">
{{ even }}
</li>
</div>
</ng-template>
```

The expanded form uses the more known Angular tools, like property binding, event binding, and two-way binding, without the asterisk

Max mentions that while we can use either the asterisk notation or the expanded form, the asterisk is preferred for its simplicity and readability

**The lesson showed us how the expanded form of `*ngFor` would look like without the asterisk, by wrapping the content in an `<ng-template>` element and using property binding on the ngFor attribute**
