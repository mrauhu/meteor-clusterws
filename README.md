# ☄ Meteor + 🚀 µWebSockets

## How to make the Meteor consume less CPU and RAM

> Use `stream-server-uws`

See also: https://github.com/meteor/meteor/pull/10120
 
## Introduction

By default, the Meteor Stream Server using the [SockJS][s] library for handling WebSocket messages of the Distributed Data Protocol (DDP).

[s]: https://github.com/sockjs

The advantage of the SockJS library is that if the WebSocket protocol are not supported by a browser, then it allows you to use alternative transports.

The disadvantage it is eating CPU and RAM, and with a large number of DDP connections and messages, the memory starts to leak.

> Can I [use WebSockets][ws] only?

[ws]: https://caniuse.com/websockets

This solution based on the ClusterWS/[cWS][c] — C++ WebSocket implementation for Node.js.
It is a fork of the [µWebSockets v0.14][u] a.k.a. `uws`.

[c]: https://github.com/ClusterWS/cWS
[u]: https://github.com/uNetworking/uWebSockets/tree/v0.14


## How to use it now

### Prerequisites

Open your project:

```bash
cd your-project-root
```

If your project not a Git repository then initialize it:

```bash
git init
```

### Installing

1. Replace [`ddp-server`][1] and [`socket-stream-client`][2], install [`disable-sockjs`][3], [`stream-server`][4] and [`stream-server-uws`][5] packages via Git:

    [1]: https://github.com/mrauhu/ddp-server
    [2]: https://github.com/mrauhu/socket-stream-client
    [3]: https://github.com/mrauhu/disable-sockjs
    [4]: https://github.com/mrauhu/stream-server
    [5]: https://github.com/mrauhu/stream-server-uws

    ```bash
    git submodule add https://github.com/mrauhu/ddp-server packages/ddp-server
    git submodule add https://github.com/mrauhu/disable-sockjs packages/disable-sockjs
    git submodule add https://github.com/mrauhu/socket-stream-client packages/socket-stream-client
    git submodule add https://github.com/mrauhu/stream-server packages/stream-server
    git submodule add https://github.com/mrauhu/stream-server-uws packages/stream-server-uws
    ```

3. Enable Stream Server with the `@clusterws/cws`, fork of the `uws`:

    ```bash
    meteor add stream-server-uws
    ```

### Usage

Run the Meteor:

```
meteor
```

### Have fun

## Thanks

* [Alex Hultman][a], author of µWebSockets;
* [Dmitrii Goriunov][d], developer of ClusterWS;
* you.

[Sergey N][mrauhu]

[a]: https://github.com/alexhultman
[d]: https://github.com/goriunov
[mrauhu]: https://github.com/mrauhu


