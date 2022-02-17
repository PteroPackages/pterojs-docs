---
description: Represents a Pterodactyl server from the Application API.
---

# ApplicationServer

```javascript
new pterojs.ApplicationServer(<client>, <data>)
```

| Parameters | Type                                             | Description               |
| ---------- | ------------------------------------------------ | ------------------------- |
| client     | ``[`PteroApp`](../application-api/pteroapp.md)`` | The application instance. |
| data       | `object`                                         | The object payload.       |

### Properties

| Name          | Type         | Description                                                                                                                  |
| ------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| id            | `number`     | The internal ID of the server.                                                                                               |
| externalId    | `number`     | The external ID of the server.                                                                                               |
| uuid          | `string`     | The internal UUID of the server.                                                                                             |
| identifier    | `string`     | A substring of the server's UUID to easily identify it.                                                                      |
| name          | `string`     | The name of the server.                                                                                                      |
| description   | `?string`    | A brief description of the server (if set).                                                                                  |
| suspended     | `boolean`    | Whether the server is suspended from action.                                                                                 |
| limits        | `object`     | The server limits (untyped).                                                                                                 |
| featureLimits | `object`     | The server feature limits (untyped).                                                                                         |
| user          | `number`     | The ID of the server owner. Use `ApplicationServer.fetchOwner` to return the full user object via `ApplicationServer.owner`. |
| owner         | `?PteroUser` | The PteroUser object of the server owner. Use `ApplicationServer.fetchOwner` to return the full user object.                 |
| nodeId        | `number`     | The ID of the node the server is on. Use `NodeManager.fetch` to return the full node object.                                 |
| allocation    | `number`     | The ID of the allocation for the node.                                                                                       |
| nest          | `number`     | The ID of the nest the server is part of.                                                                                    |
| egg           | `number`     | The ID of the egg for the server.                                                                                            |

### Methods

#### updateDetails(options)

Updates details of the server.

| Parameters | Type     | Required | Description             |
| ---------- | -------- | -------- | ----------------------- |
| options    | `object` | true     | Update details options. |

Returns: **ApplicationServer**

#### suspend()

Suspends the server.

Returns: **Promise\<void>**

#### unsuspend()

Unsuspends the server.

Returns: **Promise\<void>**

#### **reinstall()**

Reinstalls the server.

Returns: **Promse\<void>**

#### **toJSON()**

Returns the JSON value of the server.

Returns: **object**
