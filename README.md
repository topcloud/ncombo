Nombo
======

Nombo is an Open Source Node.js framework that allows you to easily build highly scalable, rich cloud applications.
Nombo is distributed under the MIT license. Please see license_mit.txt for details. Visit http://nombo.io for more information.

To install, run:

```bash
npm install -g nombo
```

Once installation is complete, to create a new app in the current directory run (replace myapp with your app's name):

```bash
nombo create myapp
```

To create a 'nombo-samples/' directory containing sample apps use:

```bash
nombo samples
```

To deploy/redeploy the Nombo framework core on its own (for example, to upgrade Nombo), use create without arguments:

```bash
nombo create
```

If you would like to contribute to the Nombo framework, you should:

1. Fork this repo.
2. Clone your forked repo to your machine.
3. Navigate to the nombo/ directory on your machine.
4. Run npm install to fetch all npm dependencies (necessary or otherwise, it will not work)
5. Make your changes, commit them and push to your fork
6. Submit a pull request

Note that to test your changes, you should run the sample apps which are inside the nombo/samples/ directory.
For example, to run the chat app from inside the main nombo/ directory, you will need to run:

```js
node samples/chat/server.node
```

Feel free to add more sample apps, especially ones that will help with testing Nombo as it matures.

==================

#### Key Features

**Scalability**
* Nombo is launched as multiple node processes - This is all automated; you just specify how many load balancers, workers and stores to use and Nombo takes care of deployment and management. This lets you use all CPU cores on your machine/instance.
* Worker processes are highly parallelized (share no resources) - This offers almost infinite vertical scalability and provides more robust and consistent performance.
* Nombo is built on a node module called SocketCluster (built on top of Engine.io) which allows you to swap out the low-level clustering logic to use any pub/sub system of your choice (default is a module called iocluster and uses a pub/sub module called nData) - You just need to provide an adapter which has the same interface as iocluster. The clustering core could simply be an adapter to a third-party cloud-based pub/sub system. This could give you unlimited horizontal scalability.

**Asset Delivery**
* All HTTP assets are automatically minified and gzipped to reduce file size.
* Server side caching greatly minimizes disk IO operations.
* Strong client side caching greatly decreases application load time on subsequent visits and reduces the stress on your server.
* Nombo lets you bundle scripts, templates, stylesheets and images (images referenced in the CSS are also automatically loaded and cached).
* Customizable preload screen which shows accurate loading percentage when your app is accessed for the first time.

**Realtime IO**
* From inside your client-side scripts you can call methods of server-side CommonJS modules called sims (Server Interface Modules). These let your clients easily interact with your backend.
* From inside sims you can react to client input by emitting events to particular sockets or sessions (a session is associated with a group of sockets belonging to the same client) or broadcast to all connected sockets.
* You can define middleware functions for various IO segments. For example there is a middleware segment for general HTTP requests one for HTTP GET requests, POST requests, one for general IO (socket) requests, for IO requests of type RPC, etc...
* You can easily store volatile in-memory data through a session object. This data will automatically be mapped to one of possibly multiple data stores based on your session ID.

**Structure**
* Client side scripts can be loaded statically (at compile time) or dynamically (at runtime).
* Client scripts have the same structure as server-side Node.js modules and Nombo sims (CommonJS) - Like Node.js modules, each script operates in its own isolated scope.
* Allows you to import scripts which have global scope (e.g. jQuery, jQuery UI, Backbone, AngularJS...) - In Nombo, these are referred to as libs (libraries).