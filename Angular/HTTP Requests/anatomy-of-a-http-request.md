# The Anatomy of a Http Request

It's important to understand the anatomy of an HTTP request because an HTTP request has several core parts

## URL (API Endpoint)

- The most crucial part of a request is the URL, the API endpoint where we send the request
  - It might be something like `"ourdomain.com/posts/1"` with the exact path depending on the specific API we're working with

## HTTP Verb

- We use HTTP verbs like **POST, GET, PUT** to define the type of request we're making
  - This tells the server whether we want to store new data, fetch data, or modify/replace existing data
- The choice of verb depends on the API we're working with, and we can find this information in the official API documentation

## Headers (Metadata)

- When sending a request, often we need to include additional metadata known as headers
- While some default headers are added by the browser and Angular, we can also add our own headers as needed

## Body

- For certain HTTP verbs like **POST, PUT, and PATCH**, we can set a request body
  - This is where we attach data related to the request, like when creating or altering new data on the server by adding or replacing it on the server, the request body allows us to send core information with the request
