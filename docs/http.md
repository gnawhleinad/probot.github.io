---
next: docs/simulating-webhooks.md
---

# HTTP Routes

Calling `robot.route('/my-plugin')` will return an [express](http://expressjs.com/) router that you can use to expose HTTP endpoints from your plugin.

```js
module.exports = robot => {
  // Get an express router to expose new HTTP endpoints
  const app = robot.route('/my-plugin');

  // Use any middleware
  app.use(require('express').static(__dirname + '/public'));

  // Add a new route
  app.get('/hello-world', (req, res) => {
    res.end('Hello World');
  });
};
```

Visit https://localhost:3000/my-plugin/hello-world to access the endpoint.

It is strongly encouraged to use the name of your package as the prefix so none of your routes or middleware conflict with other plugins. For example, if [`probot/owners`](https://github.com/probot/owners) exposed an endpoint, the plugin would call `robot.route('/owners')` to prefix all endpoints with `/owners`.

See the [express documentation](http://expressjs.com/en/guide/routing.html) for more information.
