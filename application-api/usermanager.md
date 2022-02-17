# UserManager

```javascript
new pterojs.UserManager(<client>)
```

| Parameters | Type                          | Description               |
| ---------- | ----------------------------- | ------------------------- |
| client     | ``[`PteroApp`](pteroapp.md)`` | The application instance. |

### Properties

| Name   | Type                                                   | Description                 |
| ------ | ------------------------------------------------------ | --------------------------- |
| client | ``[`PteroApp`](pteroapp.md)``                          | The application instance.   |
| cache  | ``[`Dict`](../structures/dict.md)`<number, PteroUser>` | The cache for this manager. |

### Methods

#### resolve(obj)

Resolves a PteroUser from an object.

| Parameters | Type                                | Required | Description                 |
| ---------- | ----------------------------------- | -------- | --------------------------- |
| obj        | `string\|number\|object\|PteroUser` | true     | The object to resolve from. |

Returns: **?PteroUser**

#### fetch(id, options)

Fetches a user from the Pterodactyl API with an optional cache check.

| Parameters | Type     | Required | Description               |
| ---------- | -------- | -------- | ------------------------- |
| id         | `number` | false    | The ID of the user.       |
| options    | `object` | false    | Additional fetch options. |

Returns: **Promise\<PteroUser>**

#### **fetchExternal(id, options)**

Fetches a user by their external ID with an optional cache check.

| **Parameters** | Type     | Required | Description                  |
| -------------- | -------- | -------- | ---------------------------- |
| id             | `number` | true     | The ID of the external user. |
| options        | `object` | false    | Additional fetch options.    |

Returns: **Promise\<PteroUser>**

#### **query(entity, filter, \[sort])**

Queries the API for a user (or users) that match the specified query filter.\
Available query filters are:

* email
* uuid
* username
* externalId

Available sort options are:

* id
* \-id
* uuid
* \-uuid

{% hint style="info" %}
Keep in mind this does NOT check the cache first, it will fetch from the API directly.
{% endhint %}

| **Parameters** | Type     | Required | Description                              |
| -------------- | -------- | -------- | ---------------------------------------- |
| entity         | `string` | true     | The entity to query.                     |
| filter         | `string` | true     | The type to filter by.                   |
| sort           | `string` | false    | The option to sort by (default is none). |

Returns: **Promise\<Map\<number, PteroUser>>**

#### create(email, username, firstname, lastname)

Creates a new Pterodactyl user account.

| Parameters | Type     | Required | Description                   |
| ---------- | -------- | -------- | ----------------------------- |
| email      | `string` | true     | The email of the user.        |
| username   | `string` | true     | The username for the account. |
| firstname  | `string` | true     | The firstname of the user.    |
| lastname   | `string` | true     | The lastname of the user.     |

Returns: **Promise\<PteroUser>**

#### update(user, options)

Updates the specified user's account.

{% hint style="info" %}
Note: the account password is needed for updating any property of the user. The current or a new password can be used.
{% endhint %}

| Parameters | Type                | Required | Description                                                                                                   |
| ---------- | ------------------- | -------- | ------------------------------------------------------------------------------------------------------------- |
| user       | `number\|PteroUser` | true     | The user to update.                                                                                           |
| options    | `object`            | true     | An object of options to change. This can be: username, firstname, lastname, email, language, and/or password. |

Returns: **Promise\<PteroUser>**

#### delete(user)

Deletes the user account from Pterodactyl.

| Parameters | Type                | Required | Description         |
| ---------- | ------------------- | -------- | ------------------- |
| user       | `number\|PteroUser` | true     | The user to delete. |

Returns: **Promise\<boolean>**
