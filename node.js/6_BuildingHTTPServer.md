### 1. **Initialize the Project**
You start by creating a new project folder and initializing it using `npm init`. This creates a `package.json` file that manages the project dependencies and scripts.

**Steps:**
- Create a new folder for the project.
- Inside the folder, run the following command in the terminal:
  ```bash
  npm init -y
  ```

This command creates a `package.json` file with default values.

---

### 2. **Create the `index.js` File**
In the root of the project, create an `index.js` file. This file will be the entry point of your application.

```bash
touch index.js
```

---

### 3. **Import the `http` Module**
Node.js has a built-in module called `http` that allows you to create an HTTP server. You'll use this module to handle incoming requests and send responses.

**Code:**
```javascript
const http = require('http');
```

---

### 4. **Create a Server**
Now you can create an HTTP server using `http.createServer()`. The callback function you pass will handle incoming requests (`req`) and send responses (`res`).

**Code:**
```javascript
const server = http.createServer((req, res) => {
    console.log('New request received!');
    
    // Set the content type to plain text
    res.setHeader('Content-Type', 'text/plain');
    
    // Send a response back to the client
    res.end('Hello from server!');
});
```

- The `createServer()` method takes a callback function with two arguments:
  - `req`: This object contains information about the incoming request (like the URL, headers, etc.).
  - `res`: This object is used to send back a response to the client.

---

### 5. **Listen on a Port**
To make your server accessible, you need to specify a port. A port is essentially a "door" through which your server listens for incoming requests.

**Code:**
```javascript
const PORT = 8000;

server.listen(PORT, () => {
    console.log(`Server started and listening on port ${PORT}`);
});
```

- The `server.listen()` method starts the server and listens for requests on the specified port (in this case, port `8000`).
- The callback logs a message to the console once the server starts.

---

### 6. **Test the Server**
Once the server is running, you can test it by visiting `http://localhost:8000` in your browser.

At this point, when you make a request to the server by visiting `localhost:8000`, the browser sends a request, and the server responds with "Hello from server!".

You'll also see the log message "New request received!" in your terminal every time you refresh the page.

---

### 7. **Log Request Headers**
The `req` object contains all the details about the request, including the HTTP headers (metadata about the request, such as the type of browser or device). You can log these headers for debugging purposes.

**Code:**
```javascript
const server = http.createServer((req, res) => {
    console.log('New request received!');
    console.log('Request Headers:', req.headers);
    
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello from server!');
});
```

When you log `req.headers`, you'll see details such as the type of content the client accepts, the user-agent (browser), and other information.

---

### 8. **Log Requests to a File (Assignment)**
As part of your assignment, you can log details of each incoming request (such as the timestamp and the request headers) into a file.

First, you'll need the `fs` (file system) module, which is also built into Node.js.

**Code:**
```javascript
const fs = require('fs');

const server = http.createServer((req, res) => {
    const log = `New request: ${req.method} ${req.url} at ${new Date().toISOString()}\n`;
    
    // Append the log to a file asynchronously
    fs.appendFile('server.log', log, (err) => {
        if (err) {
            console.error('Failed to write to file');
        }
    });

    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello from server!');
});

server.listen(8000, () => {
    console.log('Server started and listening on port 8000');
});
```

- **Explanation**:
  - `fs.appendFile()` appends a new log entry to the `server.log` file.
  - The log includes the HTTP method (`GET`, `POST`, etc.), the URL requested, and the current timestamp.
  - If the file doesn’t exist, Node.js will create it automatically.
  - If an error occurs while writing to the file, it logs the error to the console.

---

### 9. **Run the Server**
You can now start your server using Node.js. Update the `package.json` to make starting the server easier by adding a `start` script:

In your `package.json`:
```json
"scripts": {
  "start": "node index.js"
}
```

Now, to start the server, simply run:
```bash
npm start
```

---

### Final Thoughts
By following these steps, you’ve created a simple yet fully functional HTTP server that listens for requests, sends responses, logs request headers, and writes request data to a file.

This is a great foundation for understanding how web servers work and how you can handle incoming requests using Node.js. As you move forward, you can extend this server to handle different types of requests (like `POST` requests), serve HTML files, or even connect it to a database.
