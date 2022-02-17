---
description: Represents a Pterodactyl server from the Client API.
---

# ClientServer

```javascript
new pterojs.ClientServer(<client>, <data>)
```

| Parameters | Type          | Description          |
| ---------- | ------------- | -------------------- |
| client     | `PteroClient` | The client instance. |
| data       | `object`      | The object payload.  |

### Properties

| Name          | Type                            | Description                                             |
| ------------- | ------------------------------- | ------------------------------------------------------- |
| isOwner       | `boolean`                       | Whether the client user is the owner of the server.     |
| identifier    | `string`                        | A substring of the server's UUID to easily identify it. |
| uuid          | `string`                        | The internal UUID of the server.                        |
| name          | `string`                        | The name of the server.                                 |
| node          | `string`                        | The name of the node the server is on.                  |
| stfp          | `{ ip: string; port: number; }` | An object containing SFTP details.                      |
| description   | `?string`                       | A brief description of the server (if set).             |
| limits        | `object`                        | The server limits (untyped).                            |
| featureLimits | `object`                        | The server feature limits (untyped).                    |
| suspended     | `boolean`                       | Whether the server is suspended from action.            |
| state         | `string`                        | The current power state of the server.                  |
| installing    | `boolean`                       | Whether the server is currently being installed.        |

### Methods

#### addWebSocket()

Adds the server to the WebSocket connection list to be established.

Returns: **void**

#### **sendCommand(command)**

Sends a command to the server terminal.

| Parameters | Type     | Required | Description          |
| ---------- | -------- | -------- | -------------------- |
| command    | `string` | true     | The command to send. |

Returns: **Promise\<void>**

#### **setPowerState(state)**

Changes the server's power state.

| Parameters | Type     | Required | Description                                                                      |
| ---------- | -------- | -------- | -------------------------------------------------------------------------------- |
| state      | `string` | true     | The power state to change to. This can be "start", "stop", "restart", or "kill". |

Returns: **Promise\<void>**
