# Angular Setup and First App

- First make sure node.js, the lite version is installed

- In command prompt/shell/terminal run `npm install -g @angular/cli`

- To create, build, and serve a new, basic Angular project on a development server, go to the parent directory of your new workspace use the following commands:

`ng new my-first-project --no-strict` will create a new folder, in the current working directory with the name you want it to be called.

> can be used without `--no-strict` and run as is, to use special strict mode but to make it easier on ourselves we use non strict mode

it will ask if you would like Angular routing but you can choose `n` for no on that since we dont want to add it yet

`cd my-first-project` If the current working directory is not the right place for your project, you can change to a more appropriate directory `cd <path-to-other-directory>`

`ng serve` to build an application and serve it locally which will usually be run in our browser as [http://localhost:4200/](http://localhost:4200/)
