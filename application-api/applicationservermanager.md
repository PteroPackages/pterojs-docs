# ApplicationServerManager

```javascript
new pterojs.ApplicationServerManager(<client>)
```

| Parameter | Type                          | Description               |
| --------- | ----------------------------- | ------------------------- |
| client    | ``[`PteroApp`](pteroapp.md)`` | The application instance. |

### Properties

| Name   | Type                                                           | Description                 |
| ------ | -------------------------------------------------------------- | --------------------------- |
| client | ``[`PteroApp`](pteroapp.md)``                                  | The application instance.   |
| cache  | ``[`Dict`](../structures/dict.md)`<number, ApplicationServer>` | The cache for this manager. |

### Methods

#### resolve(obj)

Resolves an `ApplicationServer` from an object.

| Parameters | Type                                        | Required | Description                 |
| ---------- | ------------------------------------------- | -------- | --------------------------- |
| obj        | `string\|number\|object\|ApplicationServer` | true     | The object to resolve from. |

Returns: **?ApplicationServer**

#### fetch(id, options)

Fetches a server from the Pterodactyl API with an optional cache check.

| Parameters | Type     | Required | Description               |
| ---------- | -------- | -------- | ------------------------- |
| id         | `number` | false    | The ID of the server.     |
| options    | `object` | false    | Additional fetch options. |

Returns: **Promise\<ApplicationServer>**

#### create(user, options)

Creates a new Pterodactyl server for a specified user.

| Parameters | Type                | Required | Description                        |
| ---------- | ------------------- | -------- | ---------------------------------- |
| user       | `number\|PteroUser` | true     | The user to create the server for. |
| options    | `object`            | true     | Server property options.           |

Returns: **Promise\<ApplicationServer>**

#### delete(server, force)

Deletes a specified server (with optional force flag).

| Parameters | Type                        | Required | Description                                 |
| ---------- | --------------------------- | -------- | ------------------------------------------- |
| server     | `number\|ApplicationServer` | true     | The server to delete.                       |
| force      | `boolean`                   | false    | Whether to force delete it from the daemon. |

Returns: **Promise\<boolean>**
