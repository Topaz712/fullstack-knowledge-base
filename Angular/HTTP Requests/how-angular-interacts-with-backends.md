# How Does Angular Interact With Backends?

- To connect Angular with a database, we should avoid storing sensitive credentials, like database access details directly in the code of our Angular app because it would be highly insecure because anyone can view the Angular code in a web browser

  - Instead, we communicate with a server, which acts as an API, this server, typically a `REST API`, manages the database interactions
    - To learn how to build a _REST API_: [https://academind.com/learn/node-js/building-a-restful-api-with/](https://academind.com/learn/node-js/building-a-restful-api-with/)

- Angular communicates with a server, which acts as an API

- The API processes our requests and communicates with the database to store or fetch data

- Angular receives data from the server in response to our requests

- Angular interacts with the API, not the database itself

This server-side logic is handled by technologies like Node.js or PHP

**Communication with the server can involve more than just database operations, like uploading files or sending analytics data so it's essential to separate front-end and back-end tasks for security and organization**

Angular handles the HTTP requests, responses, and data interaction with the server

In this course, we'll use a REST API, the most common API type, it's similar to browsing a regular website, but when we visit its URLs, we don't receive HTML web pages and instead, we get data in formats like JSON

For practicing, we will use a dummy backend, but in a real application, we would replace it with a live backend
