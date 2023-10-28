# Setup

In `app.module.ts` we import the _ReactiveFormsModule_ This module is necessary to work with reactive forms:

`import { ReactiveFormsModule } from '@angular/forms';`

In `app.component.ts` we import the _FormGroup class_ and declare a property named signupForm of type FormGroup
This property will hold our form:

`import { FormGroup } from '@angular/forms';`
`signupForm: FormGroup;`
