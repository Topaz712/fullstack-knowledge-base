# Chaining Multiple Pipes

In Angular, we can combine multiple pipes to format data but the order of the pipes is crucial as they are applied from left to right when chaining pipes to ensure correct execution and data transformation

- We use the pipe symbol `|` to chain pipes
  - The order of application matters

So we must apply the pipes in the order we want to transform our input

Like for the Date formatting and then converting it to uppercase like so:

In _app.component.html_:
`{{ server.instanceType | date: 'fullDate' | uppercase }}`

_Incorrect Chaining_ would be that applying pipes in the wrong order can lead to errors like trying to uppercase a date, which is not a string, _leads to errors_ `{{ server.instanceType | uppercase | date: 'fullDate' }}`
