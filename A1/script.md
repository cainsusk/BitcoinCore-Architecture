# Bitcoin
Bitcoin is a unit of currency used to send, receive, and retain value among
participants on the Bitcoin Network.

Users on the Bitcoin network communicate directly with each other, rather than
through a central server, in what's known as a Peer To Peer architecture.

Users can access the network by running the Bitcoin Core protocol on nearly any
computing device.


# Bitcoin Core
Bitcoin Core is the primary system for facilitating transactions using Bitcoin.
It is the authoritative source for how each part of the technology should be
implemented.

Bitcoin Core uses a Peer to Peer (P2P) architecture where users validate each
others' transactions using a shared `blockchain` -- rather than through
a centralized server


# Block Chain
The `Blockchain` is a public record of all transactions made using Bitcoin.

It is created through computationally expensive operations that generate
a unique `block` which can be identified with a hash and contain the
transactions made at a given time. Each block is `backlinked` to it's `parent`
block.

The `blockchain` can be thought of as a stack, where the newest block is placed
on top.

# Blocks
Blocks are a data structure which have two components: the header, and body.

The header contains information for identifying a block -- whereas the body
contains information about the transactions the block represents.


# Nodes
The `blockchain` is transmitted and maintained by nodes, which are computer
systems connected to the Internet & running the Bitcoin core protocol.

A node can have the functions of: Miner, Full `Blockchain`, Wallet

Additionally, all nodes have the function to communicate with other nodes on
the network.

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


# Functional Architecture
In a functional sense, Nodes can be understood to have a layered architecture.
Each node is made up of three layers:

 - The User Interface
 - Local Bitcoin Core Protocol
 - The Connection Layer


## User Interface
The user interface is any client app using the Bitcoin Core protocol. This is
the way that users interact with Bitcoin Core and it's network.

## Bitcoin Core Protocol
The protocol can be any variation of nodes: Light, Full, Miner. This is the way
the user interface performs functions defined by the Bitcoin Core protocol.

Through this layer, Bitcoin can be generated with a miner -- or spent and
validated bu full or half nodes.

This layer also manages the user's keys in their wallet.

## Connection Layer
The connection layer is the way a Bitcoin client interfaces with the rest of the
nodes in the Peer to Peer network.


# Wallet
A node can contain a user wallet, which is the primary way a user manages
their Bitcoin and make transactions.

Wallets do not contain coins, but rather "keys" which prove ownership of coins
on the network. Users "spend" their money by signing transactions with keys in
their wallet. Keys are only stored in wallets, and not on the network.

Bitcoin Core uses nondeterministic wallets, where the keys are generated
randomly, and have no relation to each other. Furthermore, while Bitcoin Core
has an implementation for wallets -- it is only recommended for debugging
purposes.


# Transactions
To establish a link to a new block, a Full/Light node first must examine the
incoming block and look for the parent block hash.

Once it finds the correct Parent block, the node has validated the incoming
block and will add it to the `blockchain`.


# Data Flow
The transaction process begins with a node broadcasting a new transactions.

This new transaction is then validated & aggregated with others from the same
time stamp by a miner. This miner then generates & broadcasts the new block with
it's proof of work -- or hash.

chosen by highest fee !!

Now, Full and Light nodes will receive this new block and attempt to verify it
by checking that no key has already unlocked it's given value on the
`blockchain`. If the block is verified -- it is then added to the `blockchain`
to be checked against the next transaction.

If the block is not verified, this means that a key in the block has already
been spent on the block chain -- and it is thus rejected.

All transactions remain in the memory pool of pending transactions until
complete -- so if a block is rejected but still contains valid transactions,
those valid ones will eventually be allocated to a new block.


# Concurrency
As transactions are broadcast, they are added to the memory pool of pending
transactions on the P2P network. These are then verified and grouped into
blocks with proof of work by miners. The new blocks are once again broadcast to
the P2P network.

Nodes then fetch blocks from the network asynchronously and
attempt to add them to their `blockchain`.

Nodes can leave and rejoin the network without issue -- accepting
the longest `blockchain` as the correct one once it joins the network.

Furthermore, if there is a conflict or discrepancy when many transactions are
occurring concurrently -- the longest `blockchain` with the most proof of work
is accepted by nodes as their `blockchain`.

# Development
The Bitcoin Core system was developed in 2009 by Satoshi Nakamoto. The project
has been open source since they left the project in 2010.

Because the project was initiated by only one person -- it is a relatively
consistent code base in terms of basic methodologies/conventions. This helped
aid the project to be taken up by more developers. (as nobody wants to work on
a spaghetti code-base.)

Like most open source projects, the responsibility division has been flexible.
This allows developers to quickly implement features which they feel passionate
about.

However, this also results in very little incentive to develop tedious or
uninteresting features.

Because of this, development of Bitcoin Core has been sporadic, with little
organization -- however there is still a concrete development process which
must be followed to contribute to the system.


# Evolution
Bitcoin Core is a decentralized system that has been in development for over 10
years. It supports various functionalities such as `blockchain`, transactions,
contracts, wallets, payment processing, and a P2P network.

Over the years, Bitcoin core has undergone various updates to their fee
handling. They have added support for priority queues, and have introduced
replace-by-fee. They allowed better user interaction with the fee handling
system, and improved fee estimation by version 23.

The wallet was also improved, as they introduced `blockchain` pruning for
storage saving, scheduled tasks for user interaction improvements, multi-wallet
support, and improved the coin selection algorithms.

They also made a few quality of life improvements.

They made a few GUI changes, which helps the human interaction with the whole
system. They also improved the ease of use for more basic of users. The support
for full hardware wallets was also added as it was sought after by the
community.

There were also a few security updates, which introduced tor support, higher
privacy protection, and improved the overall security of the wallet.

For the future, they plan to add Bitcoin script support, updating legacy code,
improving storage efficiency, and improving the old security features. They are
also interested in Quantum computing, as it is an up and coming reality that
the Bitcoin core team will have to deal with.


# Lessons Learned
Through poring over documentation we were able to derive and comprehend the
conceptual architecture of Bitcoin Core. We found that the texts were
dense and sometimes hard to initially understand -- however once we pruned the
information down to what was strictly necessary, the conceptual architecture
became much clearer.

Our research has taught us not only how Bitcoin works, but on a deeper level it
has also taught us how to research more effectively through carefully selecting
and pruning sources.

# Limitations
As of now, this report does not go into detail about the specific mathematical
processes and implementation of Bitcoin Core -- but rather outlines the
conceptual architecture which it follows.

However, the implementation of the system is critical to understanding how
Bitcoin Core works, and must be explored further to get a firmer grasp of how
the system operates fully.


# Conclusion
Thus, Bitcoin Core is a Asynchronous, Peer to Peer system which takes advantage
of cryptography to send, receive, retain, and verify value over the internet --
without the need for third party verification.

Crucially, this provides greater freedom and security to users -- allowing them
to trust that no biased third party will influence the **objective** process of
transaction verification.
