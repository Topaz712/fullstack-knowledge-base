# Configuring the TypeScript Compiler

when executing `npx tsc` we usually have to add a TypeScript file to target `npx tsc with-typescript.ts` but sometimes we want to compile all our ts files in one go and we'll want to know how the TS compiler behaves.

we can do this by adding a TypeScript compiler config file and we do this with `npx tsc --init`
This will add a `tsconfig.json` file

**But once we work with Angular we wont need to do that because a Angular project will get TypeScript configuration files out of the box and you should only really change them if you know what you're doing**

In the typescript configuration file we have many options we can set, and an important one of is `"strict": true,` and by default is always set to true, an example of one strict type checking is that it will not allow many things like infer the values type, it must be explicitly set a type.
