# Getting Started

## Installing

The package is currently only available on NPM however additional support is coming soon!

```
$ npm install @devnote-dev/pterojs
```

{% hint style="warning" %}
NodeJS v14 or above is required for this package.
{% endhint %}

## Connecting to Pterodactyl

Pterodactyl's API is split into 2 sections: the Application API for interacting with the panel at a global scope; and the Client API for interacting with user-specific servers.

{% hint style="info" %}
The application and client API require 2 different API keys to interact with. You can find them here:

* Application: https://pterodactyl.panel.url/admin/api
* Client: https://pterodactyl.panel.url/account/api

Note that if you are not an administrator you will need to request an application API key from one.
{% endhint %}

### Using the Application API

```javascript
const { PteroApp } = require('@devnote-dev/pterojs');

// Initialising the application
const client = new PteroApp('pterodactyl.panel.url', 'pterodactyl_api_key');

// Connecting to Pterodactyl
client.connect();

// Accessing information
client.servers.fetch('evuk98yu').then(console.log);
```

### Using the Client API

```javascript
const { PteroClient } = require('@devnote-dev/pterojs');

// Initialising the client
const client = new PteroClient(
    'pterodactyl.panel.url',
    'pterodactyl_api_key',
    { ws: true }
);

// Adding servers to listen for
client.addSocksetServer([ 'kgujg66h', 'avipgt6e' ]);

// Listening to events
client.on('statusUpdate', (server, status) => {
    console.log(server);
    console.log(status);
});

// Connecting to Pterodactyl
client.connect();
```

You can find a full list of the Application and Client API's methods in the API section of the docs.
