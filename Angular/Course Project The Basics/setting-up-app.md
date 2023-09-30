# Setting up the Application

After creating our angular app we can add a bootstrap css framework so we have some css classes for the app to have nice styling, this helps so we can focus on the Angular project building and not the styling!

If angular is not downloaded into your system then in the command prompt or the vscode terminal in my case you download it with `npm install -g @angular/cli@latest` only the @latest is optional to download the latest version but make sure node.js is already installed on your computer first.

Then create a new project with
`ng new my-project-name`

`ng new my-project-name --no-strict` is the way we are doing it though so strict mode isn't enabled upon creating the project

But do `ng new my-project-name --skip-git`
if you already have a git repository and dont want to create a new one with this

Then it after its all loaded do
`cd my-project-name` to change directory into your new project

For Max's project the bootstrap we downloaded was
`npm install --save bootstrap@3` for version 3

- Now in the `angular.json` file we need to add Bootstrap to the `styles[]` array and the path is `node_modules/bootstrap/dist/css/bootstrap.min.css`

- Finally `ng serve` to open http://localhost:4200/ to see the new application running
  > this will build an application and serve it locally
