# What are Services and Dependency Injection?

- In Angular, services are special and help our app perform specific tasks or provide data to different parts of our application
- They help us keep our code organized and make it easier to share functionality across various components
- Services help different parts of your Angular app communicate and share functionality
- It's basically another piece in our Angular app, another class we can add which acts as a central repository/central business unit, something we where we can store data
- So instead of each component handling its own logging or data storage, they can use specialized services like LogService and UserService to do these tasks, making our code reusable and maintainable

## App Component

The main component in our application, often referred to as the root component. It's responsible for managing the overall structure of our app

## AboutComponent

This is a component in our appcomponent
It's using services to log data to the console, which means it's using a service called LogService to handle logging

## UserComponent

A component in our appcomponent, responsible for managing user-related tasks
It uses a service called UserService to store user data

### User Detail Component

A component in our UserComponent, for displaying detailed user information
It also logs data to the console

# Log Service

A service responsible for handling logging tasks, like writing messages to the console.

# User Service

A service responsible for managing user data storage and retrieval
It provides functionality to store and retrieve user-related information
