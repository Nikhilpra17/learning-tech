### What is a URL?
URL stands for **Uniform Resource Locator**. It's essentially a human-readable address that directs a user to a specific resource, such as a webpage, on the internet. Behind every URL is an IP address, but because IP addresses are difficult for humans to remember, URLs offer a friendly way to access resources online.

### Major Components of a URL:
A typical URL has several important components:
1. **Protocol**: This indicates the set of rules used to communicate between the browser and the server. For example, HTTP (Hypertext Transfer Protocol) or HTTPS (the secure version of HTTP). 
    - HTTP: Used for regular data transfer.
    - HTTPS: More secure and uses SSL certificates for encryption.

```html
https://www.example.com
```

In this case, `https` is the protocol that ensures the data transferred between the user and the server is encrypted.

2. **Domain Name**: This is the human-friendly name of a website (like `google.com` or `youtube.com`). The domain name is translated into an IP address, which is used by the server to locate the resource. Domain names help in avoiding the need to remember long and complicated IP addresses.

3. **Path**: After the domain, the **path** specifies the exact location of the resource on the server.
   
   Example:
   ```html
   https://www.example.com/about
   ```
   In this URL, `/about` is the path that points to the "About" page of the website.

4. **Query Parameters**: These provide additional information to the server about the request, typically in the form of key-value pairs.
   
   Example:
   ```html
   https://www.example.com/search?q=javascript
   ```
   Here, `?q=javascript` is a query parameter where `q` is the key and `javascript` is the value. Query parameters are separated by `&` if there are multiple pairs.

5. **Fragment**: Sometimes, URLs can also have a **fragment identifier** which typically points to a specific section of a webpage. It comes after a `#` in the URL.

Example:
```html
https://www.example.com/about#team
```
In this case, `#team` is a fragment that would take the user directly to the "Team" section of the page.

---

### Code Example: Parsing a URL in Node.js
In the video, the speaker explains how to parse a URL and extract its components using Node.js. The `url` package in Node.js is used for this purpose.

First, install the `url` package:
```bash
npm install url
```

Then, you can use it to parse a URL string:
```javascript
const url = require('url');

const myUrl = url.parse('https://www.example.com/about?userId=1&name=JohnDoe');
console.log(myUrl);
```

The `url.parse()` method breaks down the URL into its components:
- `protocol`: `'https:'`
- `host`: `'www.example.com'`
- `pathname`: `'/about'`
- `query`: `'userId=1&name=JohnDoe'`

### Nested Paths:
The speaker also explains **nested paths**. For example, URLs can have nested routes like:
```html
https://www.example.com/projects/project1
```
In this case, `/projects/project1` is a nested path. This can help in organizing resources and pages hierarchically on the website.

### Example of Handling URL Paths in Node.js
The speaker shows how to handle different URL paths using the `http` module in Node.js. Here's an example of how to handle a simple request:

```javascript
const http = require('http');
const url = require('url');

const server = http.createServer((req, res) => {
    const parsedUrl = url.parse(req.url, true);
    const path = parsedUrl.pathname;
    const query = parsedUrl.query;

    if (path === '/about') {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.write('<h1>About Page</h1>');
    } else if (path === '/contact') {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.write('<h1>Contact Page</h1>');
    } else {
        res.writeHead(404, { 'Content-Type': 'text/html' });
        res.write('<h1>Page Not Found</h1>');
    }
    res.end();
});

server.listen(8000, () => {
    console.log('Server is running on port 8000');
});
```

### Handling Query Parameters
In this example, query parameters are handled using `parsedUrl.query`:
```javascript
if (path === '/search') {
    const searchTerm = query.q;
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.write(`<h1>Search Results for: ${searchTerm}</h1>`);
    res.end();
}
```
If a user visits `http://localhost:8000/search?q=javascript`, the server responds with:
```
Search Results for: javascript
```
