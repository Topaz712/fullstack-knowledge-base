# How Authentication Works

- Authentication is crucial for web applications, it involves validating user credentials, not just entering email and passwords

  - It involves understanding the technical workings behind the scenes

- Our application involves a client 'browser' and a server
  - User credentials like email and password are sent to the server for validation
    - Validation doesn't happen in the browser due to security concerns
    - Browsers are insecure for validation due to exposed JavaScript sbecause users can manipulate or disable JavaScript

Angular's Single Page Applications "SPA's" decouple front end from the back end for the different pages, rendering traditional sessions for different Url's impractical

- Our back end/our server will be a RESTful API and not a server that renders HTML pages we're on, rendering sessions impractical
  - RESTful API's and GraphQL are both stateless

The server doesn't store session data communication happens through the Angular HTTP client

- Instead of sessions, tokens are used for authentication and the server validates the user's credentials

  - If valid, _the server generates a token 'JSON Web Token - JWT'_
    - They replace sessions, providing security and flexibility

- A Token is an encoded string with metadata

  - It's encoded not encrypted, which means the string can be unpacked and read by the client
  - It's generated on the server with a specific algorithm and a secret key which only the server knows and only the server can validate incoming tokens for their validity

- Clients 'browsers' store tokens like in the local storage of the browser and attaches them to authenticated requests

  - Instead of sessions, tokens are used
  - The server validates user credentials and sends an encoded token which is necessary for accessing protected resources like storing recipes

- Security lies in the server's knowledge of the algorithm and private key
- Having server side control ensures security because tokens cannot be generated or altered on the client

- Implementation's initial steps involves creating a user interface for credentials like a user signup and login
- Logic is gradually added to generate, store, and attach tokens to requests
  - The subsequent steps focus on the logic for token creation and attachment to requests

Token-based authentication enhances security, allowing controlled access to protected resources
