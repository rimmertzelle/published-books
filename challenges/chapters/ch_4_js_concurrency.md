# Concurrency and Cors

In JavaScript, concurrent requests refer to initiating multiple asynchronous operations at the same time, typically to improve performance by not waiting for one task to complete before starting the next.

## Concurrency vs. Parallelism
Concurrency: Tasks are started independently and can be in progress at the same time, but not necessarily executing at the exact same moment.
Parallelism: Tasks are executed simultaneously, usually on different processors or cores.
In JavaScript (which is single-threaded in the browser), we achieve concurrency using asynchronous APIs like fetch, setTimeout, or Promise.

Example in JavaScript

```javascript
async function getData() {
  const request1 = fetch('https://api.example.com/data1');
  const request2 = fetch('https://api.example.com/data2');

  const [response1, response2] = await Promise.all([request1, request2]);

  const data1 = await response1.json();
  const data2 = await response2.json();

  console.log(data1, data2);
}
```
Here’s what happens:
1. request1 and request2 are started concurrently.
2. Promise.all waits for both to finish.
3. We only await both once, not one after the other.

Improved example using async/await
```javascript
const response1 = await fetch('https://api.example.com/data1');
const response2 = await fetch('https://api.example.com/data2');
```

## Cors

Why CORS Is a Headache

CORS is a browser security feature that restricts web pages from making requests to a different domain (origin) than the one that served the web page.

For example:
If your frontend app is running at http://localhost:3000, and you try to fetch data from https://api.example.com, the browser treats it as a cross-origin request.

Unless the external API explicitly allows your origin, the browser will block the request for security reasons.

### Common Solutions to CORS Issues

1. API Supports Cors - configure it correctly
If you control the API, set the correct CORS headers:
```http
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Headers: Content-Type
```
In the [article repository](https://github.com/HZ-HBO-ICT/articles/blob/main/src/routes/index.ts) we used this setup in two routes via the cors middleware package.
```javascript
router.get('/articles', getArticles);
router.get('/articles/:id', getArticle);
router.get('/tags', Cors(), getTags);
router.get('/tags/:id', Cors(), authenticateToken, getTag);
```


2. Use a Proxy Server
Forward your requests through a server you control. Since CORS is enforced by browsers, this sidesteps the issue.

Backend
```javascript
app.use('/api', createProxyMiddleware({
  target: 'https://external-api.com',
  changeOrigin: true,
  pathRewrite: { '^/api': '' },
}));
```
Frontend
```javascript
fetch('/api/resource')
```
In the [second monolith example](https://github.com/HZ-HBO-ICT/my-second-monolith/blob/main/src/controllers/indexController.ts) we executed the request on a node server instead of the client and forwarded the data to the client via the render method.

```javascript
import { getData } from '../utils/ajax.js';

export const getIndex = async (req: Request, res: Response): Promise<void> => {
  const article: ArticleResponse = await getData('http://localhost:3012/articles/1');
  res.render('index', { article: article });
};
```

### Please remember
CORS is a browser-side security feature — you won't face it in:

- Backend services
- Postman
- curl
- It only affects frontend code running in the browser.
