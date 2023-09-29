# Outputting Lists with ngFor

`*ngFor=""` requires an asterik because it is a structural directive, changes or modifies the DOM

The ngFor base syntax:

`*ngFor= "let server of servers"`
We define a temporary variable inside the loop with let, then with the property we defined in the TypeScript file that we want to loop through all elements in this array and assign individual elements to the dynamic server variable

- Now the variable can be used in the template
