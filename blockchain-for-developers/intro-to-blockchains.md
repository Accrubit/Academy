---
description: >-
  Understand the technical components of a blockchain and how they work together
  to create a persistent and distributed immutable ledger.
---

# Technical Intro to Blockchain

### Getting Started

{% hint style="info" %}
### What this section covers

* Blockchain Basics
* Distributed P2P Networks
* Digital Ledgers: Traditional
* Byzantine Generals Problem
* Digital Ledgers: Blockchain
* Cryptographic Hashes
* Blockchain Mining
* Consensus Methodologies
{% endhint %}

This module is going to be technically heavy, but don't become discouraged as most of the components by themselves are fairly simple to understand. 

{% hint style="danger" %}
**Don't skip ahead.** 

Focus on one component at a time until you understand it, because everything on this page is required knowledge before we can begin developing a blockchain of our own. 
{% endhint %}

![](../.gitbook/assets/weekly-market-breakdown-7.png)

Blockchain was first invented with the development of the cryptocurrency Bitcoin, which is a peer to peer digital currency and settlement network that enables individuals to store, retrieve, and transact anywhere in the world across any border without needing a 3rd party to facilitate the service. [\[1\]](https://bitcoin.org/bitcoin.pdf)  
  
It's important to note, that Bitcoin and blockchain are not synonymous with each other anymore. Blockchain is the underlying software design that enables Bitcoin to exist, but like any other software product there are many different variations on the market. [\[2\]](https://www.ibm.com/blogs/blockchain/2017/05/the-difference-between-bitcoin-and-blockchain-for-business/)  
  
Due to this, there are hundreds of definitions for blockchain circulating around the internet, most of which are inaccurate or over simplified. As a blockchain developer, the below definition is what you want to actually remember. [\[6\]](http://fortune.com/2017/12/07/satire-its-time-to-admit-no-one-knows-what-the-blockchain-is/)

### Blockchain Defined

{% hint style="info" %}
A blockchain is a chronologically sorted, distributed, digital ledger which contains an irreversible archive of transaction records that are stored and chained together using cryptography in batches called blocks.
{% endhint %}

![Blockchain Visualization](https://www.accrubit.com/uploads/2/8/3/7/28374731/published/1_1.png?1527752794)

For those familiar with data structures, you could roughly describe a blockchain as a linked list of data containers holding Merkle hash trees of records.

So now that we know what a blockchain is, we can begin breaking down some of the components in this definition. The first we will start with is the block.

### Blocks Defined

{% hint style="info" %}
A block is a data container which uses a Merkle tree data structure to store cryptographic links to it's underlying records using hashes. 
{% endhint %}

**The following is a list of basic block components:**

* **Header**
  * Parent Block's Hash
  * Merkle Tree Root
  * Block Hash
* **Records**
  * Transaction Origin
  * Transaction Destination
  * Transaction Data
* **Consensus Data**
  * Nonce
  * Timestamp

A block header basically contains all of the metadata necessary for the blockchain and node participants to validate and append a block of data to the blockchain. The previous block's hash is used to create the current block's hash, which when appended to the blockchain creates a chronological chain of blocks starting from the genesis block. 

This is why it's called a blockchain, because each consecutive block is linked to the previous block through hashes. Below is an example of a block header for Bitcoin block \#547,634.

![https://www.blockchain.com/](../.gitbook/assets/client-server-1.png)

The hash for this block was created by hashing the previous block's \(547633\) hash value. The merkle root represents the data of every record and every transaction contained in the block. You can view this data manually through queries, or you can use a block explorer to view it.

#### What's a Genesis Block?

The genesis block is the very first block in a blockchain, and since it does not have a previous block to build an identifying hash from, it is defined instead in the software itself during development. It contains parameters such as the mining difficulty, chain configuration, etc and is always considered block\[0\], much like an beginning value in an array.  You could look at it as the “settings” for your blockchain. 

For example, below is a JSON file for a genesis block configuration for an Ethereum based blockchain:

{% code-tabs %}
{% code-tabs-item title="Genesis.json Example" %}
```javascript
{
  "config": {
      "chainId": 0,
      "homesteadBlock": 0,
      "eip155Block": 0,
      "eip158Block": 0
    },
  "alloc"      : {},
  "coinbase"   : "0x0000000000000000000000000000000000000000",
  "difficulty" : "0x10500",
  "extraData"  : "",
  "gasLimit"   : "0x2fefd8",
  "nonce"      : "0x000000000000032",
  "mixhash"    : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp"  : "0x00"
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

If you don't understand the above, don't worry. We will be covering the development side extensively in later modules. What's important right now is that you know the above file represents a genesis block, which is the first block in a blockchain, and contains the settings for how the blockchain will run.

Since we can visualize a blockchain in chronological order from the genesis block, we also have what is called the block height, which is simply the count from 0 \(Genesis\) to the last block appended to the chain. 

Next we have to talk about Merkle roots and Merkle trees, which is the basis for all data storage and indexing in a blockchain.

{% hint style="info" %}
### Merkle Trees Defined:

A Merkle tree is typically a binary hash tree that is created by repeatedly hashing pairs of nodes, starting from the bottom of the tree, up until there is only one hash left. This last hash is called the Merkle Root and represents all of the data in the tree.
{% endhint %}

On a blockchain the data record being hashed is called a transaction. Depending on what your blockchain is for, the data in these transactions can vary greatly. With Bitcoin they contain cryptocurrency transfer amounts and wallet addresses, but in another blockchain it could be car transfers between two dealerships.

![Merkle Tree Example](../.gitbook/assets/client-server-2.png)

#### So why use Merkle trees?

Since a Merkle root can represent a vast number of records, data can be reconstructed rapidly for fast access, and consensus protocols can quickly verify and accept that a block has integrity due to the cryptographic links from top to bottom. 

This makes it so that not even a single transaction record can be modified without making the entire block, and subsequent blockchain invalid. 

Blockchains also can use varying amounts of Merkle trees per block. For example:

* Bitcoin uses 1 Merkle tree for the storage of all transaction data.

![Bitcoin Merkle Tree](https://blog.ethereum.org/wp-content/uploads/2015/11/mining.jpg)

* Ethereum uses 3 Merkle trees for:
  * Transactions
  * Transaction Receipts 
  * State

![Ethereum Merkle Trees](https://blog.ethereum.org/wp-content/uploads/2015/11/ethblockchain_full.png)

Now you may look at the above diagram and notice there is only two trees here. This is because the third tree is much more complicated in Ethereum and uses what is called a Patricia Tree to manage the state of the Ethereum blockchain. This is beyond the scope of this guide, but if you want to rack your brain around it, just head over to ethereum.org.

### Transactions Defined

{% hint style="info" %}
A transaction is an atomic event allowed by the underlying protocol to make an addition to the state of the blockchain.
{% endhint %}

As stated before, transactions can really contain anything so long as they adhere to the rules of the blockchain outlined in the Genesis block. For example:

This could be monetary transactions where Bob sends X currency to Alice. How the blockchain interprets this transaction is the blockchain subtracts X currency from Bob and adds X currency to Alice. So to make this happen we need at least a few things:

* Bob's Address \(Transaction Originator\)
* Alice's Address \(Transaction Destination\)
* Currency Data \(Transaction Data\)

Even though we consider this a monetary transaction, what is really happening is we are modifying the state of the ledger to reflect the authorized addition and subtraction event to take place. Bob isn't actually giving anything to Alice from a technical standpoint, but instead the blockchain is updating itself based on a valid and authorized transaction. Like any software, we can create whatever events we want. 

* This could be the destruction and construction of a trade-able asset in a game.
* This could be the resolution of a name to a wallet address.
* This could be taking a file and storing it.

The list goes on.

Now I used the word authorized on purpose when talking about transaction events, because this also implies that some authentication needs to take place as well. Like any IT system containing valuable data, we should have a way to authenticate at least the originator of a transaction before allowing any authorized changes to the state occur.

In most blockchains, this authentication component takes the form of a wallet. 

This is where transactions get tricky. In order to authorize a transaction, we need to read the entire chain for the originating member in order to know the exact state of any required parties in the transaction process. So with Bob, we need to read the entire blockchain and sum his entire transactions in order to know whether he has enough of X currency to be sending to Alice prior to it being appended to the blockchain. 

This specific scenario is important, and is known as the Double Spending Problem















