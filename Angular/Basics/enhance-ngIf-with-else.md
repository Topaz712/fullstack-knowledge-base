# Enhancing ngIf with an Else Condition

`<ng-template></ng-template` is a built in Angular component that allows us to mark places in the DOM

To show it conditionally, we enhance `*ngIf` with an `else` and then noServer
`<p *ngIf="serverCreated; else noServer">`

## So basically `*ngIf` with `"else"` in Angular helps us show different things on our webpage based on whether a condition is true or false
