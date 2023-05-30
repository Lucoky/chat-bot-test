# Software Developer Test - Websocket Catalog

## Objective
Create a websocket application that handles session authentication, retrieves a catalog of products, and allows the user to interact with the catalog by selecting items, navigating through pages, or specifying a page number.

## Requirements

1. When a client establishes a websocket connection, the server should generate a UUID token for the session and return it to the client.
2. The websocket should send a response containing the catalog of products available for sale upon successful authentication.
3. The client should be able to interact with the catalog by selecting items, navigating through pages, or specifying a page number.
4. The server should handle the client's actions and respond accordingly, providing the requested information.

## Example WebSocket Connection

To connect to the websocket server and receive the session token and catalog, you can use the following example code in JavaScript:

```javascript
const socket = new WebSocket('wss://example.com/websocket');

socket.addEventListener('open', function (event) {
  console.log('WebSocket connection established.');

  // Sending a request to generate a session token
  socket.send(JSON.stringify({ action: 'generateToken' }));
});

socket.addEventListener('message', function (event) {
  const message = JSON.parse(event.data);

  // Handling different types of responses from the server
  switch (message.type) {
    case 'token':
      const token = message.data.token;
      console.log('Received session token:', token);
      break;
    case 'catalog':
      const catalog = message.data.products;
      console.log('Received catalog of products:', catalog);
      break;
    case 'topList':
      const topList = message.data.products;
      console.log('Received top list of products:', topList);
      break;
    default:
      console.log('Received unknown message:', message);
  }
});

socket.addEventListener('close', function (event) {
  console.log('WebSocket connection closed.');
});
```
## Evaluation Criteria

- Correct implementation of websocket authentication and session management.
- Proper retrieval and transmission of the product catalog upon successful authentication.
- Ability to handle and respond to user actions, such as item selection, navigation, and page specification.
- Code cleanliness, readability, and adherence to best practices.
- Proper error handling and graceful disconnection of clients.

## Additional Guidelines

- You can choose any programming language or framework of your preference.
- You may use any libraries or tools you deem necessary to complete the task.
- Please include a README file with instructions on how to run your application and any additional information you would like to provide.

## Submission

Please submit your solution as a repository on a version control platform (e.g., GitHub, GitLab) and share the repository link with us. Make sure the repository is accessible, and include any instructions necessary for us to evaluate your solution.

Good luck, and have fun!
