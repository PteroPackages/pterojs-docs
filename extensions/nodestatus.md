---
description: A node status tracking extension from PteroJS
---

# NodeStatus

## Getting Started

The status tracking extension is designed to be easily integratable with any application. It does not come with predefined templates, leaving the design and control of the tracker up to you.

{% hint style="info" %}
A Pterodactyl Application API key is needed for this extension. To get one go to your panel's admin page and create one: https://pterodactyl.panel.url/admin/api.
{% endhint %}

```javascript
const { NodeStatus } = require('@devnote-dev/pterojs');

// Initialise the class
const status = new NodeStatus({
    domain: 'PTERO_DOMAIN',
    auth: 'PTERO_APPLICATION_API_KEY',
    nodes: [2, 3],
    callInterval: 60,
    retryLimit: 2
});

// Connect to the API
status.connect();
```

| Parameter    | Type       | Description                                                                    |
| ------------ | ---------- | ------------------------------------------------------------------------------ |
| domain       | `string`   | The domain URL which links to the Pterodactyl panel.                           |
| auth         | `string`   | The Application API key.                                                       |
| nodes        | `number[]` | The IDs of the nodes to listen for.                                            |
| callInterval | `number`   | The time in seconds to wait between API calls (between 30-6000 seconds).       |
| nextInterval | `number`   | (Optional) The time in seconds to wait between processing checks (default: 5). |
| retryLimit   | `number`   | (Opional) The amount of times to retry calling the API (default: 0).           |

{% hint style="info" %}
If set, the nextInterval must be less than the callInteval. This is to prevent processing overflow when the next API calls are being made.
{% endhint %}

## Events

NodeStatus emits 4 different events: connect, interval, disconnect, and debug. The first 3 are node related, whereas the debug event is for logging the background processes of the tracker.

The connect, interval and disconnect events also have corresponding properties (referenced as a call property) which can be used to respond to the event. Please note that the event will always be emitted first before the call property is executed.

### Connect

This event is emitted when the tracker connects or reconnects to a node. Currently only contains the ID of the node and it may be expanded to a `reconnect` event in future which has the full node payload.

#### Example response handler

```javascript
status.on('connect', id => {
    console.log(`Connected to node ${id} of 4`);
}

// or alternatively use the call property
status.onConnect = id => {
    console.log(`Connected to node ${id} of 4`);
}

// Output:
// Connected to node 1 of 4
```

### Interval

This event is emitted at each [nextInterval](nodestatus.md#getting-started) with a node payload object. Keep in mind this object is not stored internally (so it wont be accessible for other events), this will likely be in a future version.

#### Example payload

```javascript
{
  id: 2,
  uuid: '8b7a2382-9416-4e49-b7aa-3e313ead7b8b',
  public: true,
  name: 'Dev 02',
  description: 'development node',
  location_id: 2,
  fqdn: 'd2.not.a-real.host',
  scheme: 'https',
  behind_proxy: false,
  maintenance_mode: false,
  memory: 12000,
  memory_overallocate: 0,
  disk: 185000,
  disk_overallocate: 0,
  upload_size: 100,
  daemon_listen: 8080,
  daemon_sftp: 2022,
  daemon_base: '/var/lib/pterodactyl/volumes',
  created_at: '2021-09-27T19:27:22+00:00',
  updated_at: '2021-09-27T19:27:22+00:00',
  allocated_resources: { memory: 5150, disk: 25550 }
}
```

#### Example response handler

```javascript
status.on('interval', node => {
    console.log(`
        Node Information
        ID: ${node.id}
        Name: ${node.name}
        Description: ${node.description}
        FQDN: ${node.fqdn}
        Memory: ${node.memory}
        Disk: ${node.disk}
    `);
});

// or with call property
status.onInterval = node => {
    console.log(`
        Node Information
        ID: ${node.id}
        Name: ${node.name}
        Description: ${node.description}
        FQDN: ${node.fqdn}
        Memory: ${node.memory}
        Disk: ${node.disk}
    `);
});

// Output:
/*
    Node Information
    ID: 2
    Name: Dev 02
    Description: development node
    FQDN: d2.not.a-real.host
    Memory: 12000
    Disk: 185000
*/
```

### Disconnect

This event is emitted when the tracker disconnects from a connected node. It only contains the ID of the node in the event.

#### Example response handler

```javascript
status.on('disconnect', id => {
    console.log(`Disconnected from node ${id}`);
}

// or using the call property
status.onDisconnect = id => {
    console.log(`Disconnected from node ${id}`);
}

// Output:
// Disconnected from node 3
```

### Debug

This event is emitted for logging the background processes of the tracker. Unlike the other events, it does not have a call property, only the event.

```javascript
status.on('debug', console.log);
```

## Closing

In the event of process termination the tracker will call the `close()` function automatically which will terminate the interval loop and clear the internal connected set. You can also call this function manually and it will execute the same way.
