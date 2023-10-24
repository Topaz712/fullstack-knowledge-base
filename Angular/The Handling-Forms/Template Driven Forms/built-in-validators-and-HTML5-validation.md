# Built-in Validators & Using HTML5 Validation

- Angular comes with several built-in validators, and we can find the complete list in the Validators class at [https://angular.io/api/forms/Validators](https://angular.io/api/forms/Validators)

  - These validators are used in both template-driven and reactive approaches

- For template-driven forms, we'll use directives as validators
  - To find the list of these validator directives, search for "validator" in the official Angular docs at [https://angular.io/api?type=directive](https://angular.io/api?type=directive), any directive marked with "D" is a directive and can be added to our template to perform validation

Additionally, it's worth knowing that Angular usually disables HTML5 validation by default, so we can enable it by adding `ngNativeValidate` to a control in our template
