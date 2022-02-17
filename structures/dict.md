---
description: >-
  (Also known as Dictionary) An extended Map with additional helper methods used
  for manager caches in the PteroJS library.
---

# Dict

```javascript
new pterojs.Dict([...iterable])
```

{% hint style="info" %}
This page will only cover methods defined in the [repository](https://github.com/devnote-dev/PteroJS/blob/main/src/structures/Dict.js). For more information about standard methods, see the [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Map).
{% endhint %}

### Methods

#### has(key)

_This is a standard method included for the sake of implementation. See the MDN reference for more information._

Returns: **boolean**

#### **get(key)**

_This is a standard method included for the sake of implementation. See the MDN reference for more information._

Returns: **?any**

#### set(key, value)

_This is a standard method included for the sake of implementation. See the MDN reference for more information._

Returns: **this**

#### delete(key)

_This is a standard method included for the sake of implementation. See the MDN reference for more information._

Returns: **boolean**

#### **some(fn)**

Checks if at least one of the items in the dict pass the function.

| **Parameters** | Type       | Required | Description                        |
| -------------- | ---------- | -------- | ---------------------------------- |
| fn             | `Function` | true     | The function to apply to the dict. |

Returns: **boolean**

#### every(fn)

Checks if all the items in the dict pass the function.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

#### hasAny(...keys)

Checks that any of the specified keys exist in the dict.

| Parameters | Type     | Required | Description            |
| ---------- | -------- | -------- | ---------------------- |
| keys       | `...any` | true     | The keys to check for. |

Returns: **boolean**

#### hasAll(...keys)

Checks that all of the specified keys exist in the dict.

| Parameters | Type     | Required | Description            |
| ---------- | -------- | -------- | ---------------------- |
| keys       | `...any` | true     | The keys to check for. |

Returns: **boolean**

#### first(amount)

Returns the first item (or items if otherwise specified) in the dict.

| Parameters | Type     | Required | Description                                               |
| ---------- | -------- | -------- | --------------------------------------------------------- |
| amount     | `number` | false    | The number of items to return from the start of the dict. |

Returns: **any|any\[]**

#### last(amount)

Returns the last item (or items if otherwise specified) in the dict.

| Parameters | Type     | Required | Description                                             |
| ---------- | -------- | -------- | ------------------------------------------------------- |
| amount     | `number` | false    | The number of items to return from the end of the dict. |

Returns: **any|any\[]**

#### random(amount)

Returns a random item (or items if otherwise specified) in the dict.

| Parameters | Type     | Required | Description                           |
| ---------- | -------- | -------- | ------------------------------------- |
| amount     | `number` | false    | The number of random items to return. |

Returns: **any|any\[]**

#### map(fn)

Applies the function to each item in the dict and returns an array of the results.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

Returns: **any\[]**

#### filter(fn)

Applies the function to each item in the dict and returns a dict of the results that passed.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

Returns: **Dict\<any, any>**

#### find(fn)

Applies a function to each item in the dict and returns the first one that passes.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

Returns: **?any**

#### sweep(fn)

Applies a function to each item in the dict and returns the number of items removed. Returns the number of items removed.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

Returns: **number**

#### part(fn)

Applies a function to each item in the dict and returns 2 dicts, the first containing items that passed the function and the second containing the failed items.

| Parameters | Type       | Required | Description                        |
| ---------- | ---------- | -------- | ---------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict. |

Returns: **Dict\<any, any>\[]**

#### reduce(fn, acc)

Reduces each item in the dict to a single value.

| Parameters | Type       | Required | Description                             |
| ---------- | ---------- | -------- | --------------------------------------- |
| fn         | `Function` | true     | The function to apply to the dict.      |
| acc        | `any`      | true     | The object to accumulate the values to. |

Returns: **any**

#### join(...dict)

Joins one or more dicts with the current one and returns the value.

| Parameters | Type      | Required | Description        |
| ---------- | --------- | -------- | ------------------ |
| dict       | `...Dict` | true     | The dicts to join. |

Returns: Dict

#### difference(dict)

Returns a dict containing the different items between both dicts.

| Parameters | Type   | Required | Description                         |
| ---------- | ------ | -------- | ----------------------------------- |
| dict       | `Dict` | true     | The dict to compare differences to. |

Returns: **Dict**
