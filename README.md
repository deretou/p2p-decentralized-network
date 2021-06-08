# P2P decentralized network
Twenty nodes peer-to-peer decentralized network

## Installation

This assignment requires you to have Python 3.7 and Docker installed on your system. If you don't already have both, please follow the instructions below:

- [Python setup instructions](https://docs.python.org/3/using/index.html)
- [Docker CE setup instructions](https://docs.docker.com/install/)

### Project setup

This codebase uses [Poetry](https://poetry.eustace.io/) to manage the Python environment and dependencies. Poetry can be installed on most systems with the following command:

```bash
curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python
```

After cloning this repo, you can use Poetry to install the dependencies:

```bash
poetry install
```

## Getting started

We have provided you with a basic template to help you get started on this assignment. This template contains a skeleton Python project, as well as a Docker Compose configuration used to bootstrap a network.

*__Important__: Although it's encouraged, you are not required to use the provided starter code or Docker. Feel free to start from scratch if you don't find it useful.*

**p2pnetClient**

The [p2pnetClient](p2pnet/client.py) class is a stub implementation of the client interface for a node. It should be able to make network calls to a `p2pnetServer`.

A `p2pnetClient` instance is initialized with the address of a node.

**p2pnetServer**

The [p2pnetServer](p2pnet/server.py) class is a stub implementation of a node's server. It should be able to respond to network calls made by a `p2pnetClient`.

## Commands

We have provided you with a simple CLI to test your solution. 

### start-network

The `start-network` command spins up a network of 16 nodes using Docker Compose. Each node runs inside its own Docker container and is exposed at a unique port number ranging from 7001-7016.

Each node is initialized with the addresses of two other peers in the network. This creates a simple network topology, but you are encouraged to find more optimal structures.

Docker will automatically build the latest version of your code, so this command can be used to test your solution as you build it.

**Example usage:**

```
poetry run p2pnet start-network
```

### stop-network

The `stop-network` command stops any nodes currently running in the test network.

**Example usage:**

```
poetry run p2pnet stop-network
```

### send-message

The `send-message` command can be used to send a message to a node in the network. This command should only be used after the network has been started with `start-network`.

**Arguments:**

- `node-number`: The node number to connect to. Must be between 1-16.
- `message`: The message to send. Must be a single phrase with no spaces.

**Example usage:**

```bash
# Send the message "apple" to node 4
poetry run p2pnet send-message 4 apple
```

### get-messages

The `get-messages` command returns all messages that have been received by a single node.

**Arguments:**

- `node-number`: The node number to connect to. Must be between 1-16.

**Example usage:**

```bash
# Get all messages received by node 8
poetry run p2pnet get-messages 8

Example output:
    - Apple (Node 1 -> Node 8 -> Node 10)
    - Banana (Node 3 -> Node 5 -> Node 10)
    - Orange (Node 7 -> Node 15 -> Node 9 -> Node 10)

```

### remove-node

The `remove-node` command stops a single node in the network.

**Arguments:**

- `node-number`: The node number to remove. Must be between 1-16.

**Example usage:**

```bash
# Stop node 9
poetry run p2pnet remove-node 9
```
