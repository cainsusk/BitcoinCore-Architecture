# Introduction
Bitcoin Core is the primary system for facilitating transactions using Bitcoin.
It is the authoritative source for for how each part of the technology should be
implemented.

Bitcoin Core uses a Peer to Peer (P2P) architecture where users validate each
others' transactions using a shared `blockchain` -- rather than through
a centralized server


# Old privacy models
The old model for privacy in transactions relied on a trusted third party to
verify transactions


# New privacy models
Whereas this new model for privacy relies on users to validate transactions,
allowing for a more democratic and equal financial system.


# Block Chain
The `Blockchain` is a public record of all transactions made using Bitcoin.

It is created through computationally expensive operations that generate
a unique `block` which can be identified with a hash and represent the
transactions made at a given time. Each block is `backlinked` to it's `parent`
block.

The `blockchain` can be thought of as a stack, where the newest block is placed
on top -- and has unbounded size.


# Nodes
The `blockchain` is transmitted and maintained by nodes, which are computer
systems connected to the Internet & running the Bitcoin core protocol.

Miner nodes are the workhorses of Bitcoin Core. They run a special version of
the Bitcoin Core protocol which contains rules for how to generate blocks. Once
a block is created, it is then broadcast to other nodes to be added to the
`blockchain`.

The process of creating blocks is the computationally expensive operation which
ensures the security of Bitcoin. 

Full nodes maintain a local copy of the block chain -- starting at the initial
block on the chain (aka the genesis block). The local copy of the chain is
constantly updated as new blocks are found and used to extend the chain.

Light nodes are nodes that maintain only a subset of the total `blockchain`
which can verify transactions using a simplified verification method.


# Wallet
A node can contain a user wallet, which is the primary way a user manages
their Bitcoin and make transactions.

Wallets do not contain coins, but rather "keys" which prove ownership of coins
on the network. Users "spend" their money by signing transactions with keys in
their wallet. Keys are only stored in wallets, and not on the network.

Bitcoin Core uses nondeterministic wallets, where the keys are generated randomly, and
have no relation to each other.


# Transactions
To establish a link to a new block, a Full/Light node first must examine the
incoming block and look for the parent block hash.

Once it finds the correct Parent block, the node has validated the incoming
block and will add it to the `blockchain`.


# Functional Architecture
Now that we understand the system in an abstract sense, let us put it all together.

When looking at the system functionally, there are several layers we can define:
 - The User Interface
 - Local Bitcoin Core Protocol
 - The Connection Layer


# User Interface
The user interface is any client app using the Bitcoin Core protocol. This is
the way that users interact with Bitcoin Core and it's network.


# Bitcoin Core Protocol
The protocol can be any variation of nodes: Light, Full, Miner. This is the way
the user interface performs functions defined by the Bitcoin Core protocol.

Through this layer, Bitcoin can be generated with a miner -- or spent and
validated bu full or half nodes.

This layer also manages the user's keys in their wallet.


# Connection Layer
The connection layer is the way a Bitcoin client interfaces with the rest of the
nodes in the Peer to Peer network.

# Development
The Bitcoin Core system was developed in 2009 by Satoshi Nakamoto. The project
has been open source since they left the project in 2010.

Like most open source projects, the responsibility division has been flexible.
This allows developers to quickly implement features which they feel passionate
about.

However, this also results in very little incentive to develop tedious or
uninteresting features.

Because of this, development of Bitcoin Core has been sporadic, with little
organization.


# Lessons Learned
Thus, through investigating the conceptual architecture of Bitcoin Core, we have
found that through leveraging math and cryptography, Bitcoin Core is able to
ensure security in a system without any third party verification. 

This is in stark contrast to any verification system before it -- and represents
a new model for ensuring security in global, safety critical systems.


# Limitations
As of now, this report does not go into detail about the specific mathematical
processes and implementation of Bitcoin Core -- but rather outlines the
conceptual architecture which it follows. 

However, the implementation of the system is critical to understanding how
Bitcoin Core works, and must be explored further to get a firmer grasp of how
the system operates fully.
