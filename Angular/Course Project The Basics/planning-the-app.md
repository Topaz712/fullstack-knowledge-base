# Planning the App

For this course project: The Basics, we are coding along with Max to build an application that will have recipes but also a shopping list

- The first step in creating an Angular application is the lay out structure

In the app we're going to have a shopping list and recipe book section, to manage our single ingredients to buy or the recipe book with our whole recipes in them.

## Root App Component

- So for this we'll need a root component to hold our overall application/our app component, every angular app has one

## Header

- A header component will be good to have so we can navigate between our two sections , it can also be hard coded into the app component but because it will contain its own business logic, in the end it'll trigger a routing action
  > So we'll aslo add a dropdown to header where it will let us store and fetch our recipes from the server.
- **Having that logic attached to the header, outsourcing it into its own component makes sense so that our logic wont be put all into the root component which mainly should only be responsible for holdin the overall app.**

## Shopping List

- Have an overall shopping list component to hold all data of said list
- Edit component to edit an existing item or adding a new one and submitting it, this can be nested inside the list component

## Recipe Book

- A recipe-list component that can show us a list of all our recipes
- RecipeComponent to hold our recipe list and detail next to each other
- Recipe item component to hold more information than just one line of HTML code
- Recipe detail component to let us see information about a recipe once we select it
- Later we might want to add a component that will let us edit existing recipes or add new ones
  "We might learn about this later since it's a bit too advanced right now and just focus on the displaying part for now"

## Things to also consider

We will have to _decide on what models we want to use in our app_, meaning what data we want to use and put them into _their own class_ so we have our type we can use later, to also _have a clear interface/definition of what our data looks like_ so our _components can easily communicate with each other_

- We'll need to define ingredients and how we want it to look like
- Also we'll need a model for the recipe to have things like title, description, and ingredients
