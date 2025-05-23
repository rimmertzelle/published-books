# 🌐 What Is a Web Server?

## 🔧 Key Components of a Web Server

1. **Server Hardware**
   1. A physical or virtual machine that handles requests. 
   2. Runs continuously and has a fixed IP address.
2. **Web Server Software** 
   1. Examples: Apache, Nginx, or a custom server built with Node.js. 
   2. Listens for incoming requests on ports (usually port 80 for HTTP and 443 for HTTPS). 
   3. Serves static files or executes dynamic scripts.
3. **File System or Backend Logic** 
   1. Stores HTML/CSS/JS files or backend code (like PHP, Python, Node.js). 
   2. Dynamic content is generated through scripts.
4. **Configuration Files** 
   1. Define which domain routes to which files or applications.
   2. For Apache: .conf files.
   3. For Node.js: usually defined in code (e.g., which route does what).
5. **Networking and Security** 
   1. Firewalls, TLS/SSL certificates (for HTTPS), reverse proxies, etc.

## 🔍 Concrete Example 1: Apache

Apache is a widely used web server, often serving static websites or PHP applications.

1. 🔧 Setup:
   1. Apache installed on a Linux server.
   2. Web root directory: /var/www/html
2. 🌐 How It Works:
   1. A visitor accesses http://example.com.
   2. Apache receives the request on port 80.
   3. Apache looks for the appropriate file in /var/www/html.
3. Apache sends index.html back to the browser.
4. 📁 Example File:
```
/var/www/html/index.html
```

## 🔍 Concrete Example 2: Node.js Web Server

Node.js is a runtime environment that allows you to run JavaScript code outside of the browser — including on servers. However, Node by itself does not include built-in web server functionality like routing or middleware.

To build a practical web server, developers commonly use a framework such as Express.js.

1. ⚙️ Example Without Express (Basic Server)
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('<h1>Hello from Node.js</h1>');
});

server.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});
```
- ✅ Shows how Node.js can create a basic HTTP server.
- ❌ Not practical for larger applications — lacks routing, middleware, and more.

2. 🚀 Example With Express (Recommended for Real Apps)

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('<h1>Hello from Express</h1>');
});

app.listen(3000, () => {
  console.log('Express server running on http://localhost:3000');
});
```

- ✅ Clean and readable routing (app.get('/'))
- ✅ Scalable with middleware, templating engines, JSON APIs, etc.
- 🔧 Requires installing Express: npm install express
