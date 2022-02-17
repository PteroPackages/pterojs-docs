---
description: The base class for the Pterodactyl application API.
---

# PteroApp

```javascript
new pterojs.PteroApp(<domain>, <apikey>, [options])
```

| Parameter | Type                                             | Description                                          |
| --------- | ------------------------------------------------ | ---------------------------------------------------- |
| domain    | `string`                                         | The domain URL which links to the Pterodactyl panel. |
| apikey    | `string`                                         | The application API key.                             |
| options   | ``[`ApplicationOptions`](pteroapp.md#typedefs)`` | Additional start-up options for the application.     |

{% hint style="warning" %}
You **must** keep your API key private at all times. Exposing this key can lead to your servers, nodes, configurations and more being corrupted and/or deleted.
{% endhint %}

### Properties

| Name      | Type                                                          | Description                                                                                                                                                        |
| --------- | ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| domain    | `string`                                                      | The domain for your Pterodactyl panel. This should be the main URL only (not "/api"). Any additional paths will count as the API path.                             |
| auth      | `string`                                                      | The API key for your Pterodactyl panel. This should be kept private at all times. Full access must be granted in the panel for the whole library to be accessible. |
| options   | `ApplicationOptions`                                          | Additional start-up options for the application (optional).                                                                                                        |
| readyAt   | `?number`                                                     | The timestamp that the application was ready at.                                                                                                                   |
| ping      | `?number`                                                     | The application's ping.                                                                                                                                            |
| users     | ``[`UserManager`](usermanager.md)``                           | The application user manager.                                                                                                                                      |
| nodes     | `NodeManager`                                                 | The application server node manager.                                                                                                                               |
| nests     | `NestManager`                                                 | The application node nests manager.                                                                                                                                |
| servers   | ``[`ApplicationServerManager`](applicationservermanager.md)`` | The application server manager.                                                                                                                                    |
| locations | `NodeLocationManager`                                         | The application location manager for nodes.                                                                                                                        |
| requests  | `ApplicationRequestManager`                                   | The requests manager for the application API. This is not for public use. Using this manually may result in unwanted modifications of your Pterodactyl panel.      |

### Methods

#### connect()

Initialises the connection to the Pterodactyl Application API.

{% hint style="info" %}
The client must be connected first before any other functions can be executed.
{% endhint %}

Returns: **Promise\<boolean>**

### Typedefs

#### ApplicationOptions

Startup options for the application API. By default, all fetch options are `false`, and all cache options are `true`. Enabling fetch and disabling cache for the same class will cancel out the request.

| Name           | Type      | Description                          |
| -------------- | --------- | ------------------------------------ |
| fetchUsers     | `boolean` | Whether to fetch all users.          |
| fetchNodes     | `boolean` | Whether to fetch all nodes.          |
| fetchNests     | `boolean` | Whether to fetch all nests.          |
| fetchServers   | `boolean` | Whether to fetch all servers.        |
| fetchLocations | `boolean` | Whether to fetch all node locations. |
| cacheUsers     | `boolean` | Whether to cache users.              |
| cacheNodes     | `boolean` | Whether to cache nodes.              |
| cacheNests     | `boolean` | Whether to cache nests.              |
| cacheServers   | `boolean` | Whether to cache servers.            |
| cacheLocations | `boolean` | Whether to cache node locations.     |
