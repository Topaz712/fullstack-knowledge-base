# To install TypeScript

1. First we go to the [TypeScript](https://www.typescriptlang.org/download) website

2. Make sure Node.js is installed first

3. If you want to install locally to a specific project you're working on to be able to use TypeScript in that project --> then you will need to open terminal in VScode to install TypeScript
   run **npm init -y** to create empty package.json file because we'll need that to install dependencies

4. If you want to install globally then run **npm install -g**

   > not necessary since it's enough where we can just install locally for individual projects

5. Now we can run **npm install typescript**

## Make sure to create a file called .gitignore and in that file type /node_modules

- This is important because if we push to git it will not push all the node module packages in our project, if someone decides to download our code they will most likely need node modules but they can just install locally themselves which is better

# To Use TypeScript

1. Invoke TypeScript compilor by running **npx tsc** and include the file that should be compiled otherwise you will get an error because it doesnt know which files to compile
   > example for correct way: **npx tsc with-typescript.ts**

- TypeScript code does not run in the browser
- We need to compile TypeScript to JavaScript and during that compilation process all our annotations will be removed because JavaScript doesn't know those annotations
- It's during this compilation step that we will be notified of potential code errors in addtion to the error we get in the IDE already, if we haven't already spotted them.
- Then it's the compiled code that will run in the browser
