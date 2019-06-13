# Blockchain 
## Overview:

    Blockchain is a shared digital ledger containing the entire history of transactions made on the network. It is a collection of linked blocks of transactions joined together by hash values created over time. The first such block is called the Genesys block. Information stored is permanent and cannot be changed.

    Blocks are invalidated whenever hash values change with data modifications. This can identify any malicious activities.


Framework topics to cover:
1. Transaction
1. Wallet
1. Signature
1. Memory pool
1. Network
1. Consensus
1. Hashing
1. Blocks
1. Encoding

## Conventional system
Before Blockchain was introduced, transactions in the real world were carried out based on a global standard which sets the value for each currency. In exchange for goods and services, people pay equivalent to money. These transactions are tracked and maintained over by the banks which act as the central authority regulating the transaction flow thus acting as a trusted 3rd party facilitating exchange between other two parties

For keeping track of all the transactions, banks maintain a ledger not necessarily on paper or digital. It is a list of all the transaction records. This allows the bank to know
* Who has money?
* Who owns the money?
* How much money is there?

This prevents the **Double Spending problem**:
> It is a problem when a person tries to use a single amount for two transactions at the same time.

Blockchain improves many of the features from the conventional system while also trying to remove or mend the unrequired ones.

### Problems with the current system
Banks seem to have absolute power on the information about our money by acting as the central authority. These records are left in the possession of the banks alone which will rarely allow others to have a look at. but that means we are forced to blindly accept whatever it states, even if there are errors, chances of fraud or some other mishappenings, they have the only copy and that makes it supreme

Instead, we can create a shared ledger with everyone having access to it ensuring proper transparency while maintaining the same level of trust and security that the banks provide.

Also, there is a chain of transactions across banks when we wish to send money from one person to another. Also, the information gets shared along the way. This also leads to a lot of delay in the transaction and there is always some fee charged for the services banks provide.

This problem can be solved by a shared ledger maintained by a blockchain network


## The one who started it all: Bitcoin
Bitcoin was the first application of Blockchain that actually introduced it as an interesting platform to explore. Understanding Bitcoin let to the foundation of the many concepts of Blockchain we see today.

>Bitcoin is a digital currency (cryptocurrency) that facilitates financial transactions through a Blockchain platform

Bitcoin uses the concept of blocks (a group of transactions to be validated) 

## Blochain Components
### 1. Hashing
    Hashing is a mathematical operation that is used to produce a unique value for the input given. A hash function is a one-way function which generates unique values which cannot be used to gain back the original input (Not without tremendous computation). A hash value can hence be used as digital fingerprint and identifier for information. A single change in the input will bring a completely different hash value (Avalanche effect)

    Bitcoin uses SHA256 hashing algorithm which generates 256-bit hash values for each block on the blockchain thus creating a unique identifier for each block
   Check out how SHA256 work on [Anders.com](https://anders.com/blockchain/hash.html)

### 2. Blocks
    Blocks are building materials of the blockchain. It holds a list of transactions to be added to the blockchain. The blockchain which is simply a list of transactions can become cumbersome to handle as no of transactions keep on increasing.

    To deal with this they are rather handled in groups called blocks.

    The block header along with the transactions complete a block. It contains :
    1. Previous block hash - For linking blocks together
    2. The timestamp of block creation - TO prevent double spending
    3. Merkle root - To maintain the integrity of the entire block
    4. Nonce - Associated with difficulty in generating hash values
### 3. Distributed peer-to-peer network
    A peer to peer network is a network of computers that allows information to be directly shared across the users without the need for a central authority

    A distributed network is a network that allows information to be spread out across many users

    A blockchain network is both peer-to-peer and distributed. Every blockchain downloads and maintains the latest copy of the blockchain (Distributed) and at the same allows everyone to participate with any other user on the network (peer-to-peer).
### 4. Memory Pool
    The memory pool (also known as the mempool) is the waiting place for transactions before they enter the blockchain. The blockchain can only handle so much information at once, and the backlog of information goes here.

    Transactions leave the mempool when they are added to blocks by miners after they are being validated. The various other reasons for transactions to leave mempool are :

    1. The transaction expired by timeout (by default 14 days after entering).
    2. The transaction was at the bottom of the mempool (when sorted by a fee), the mempool had reached its size limit, and a new higher-fee transaction was accepted, evicting the transaction at the bottom.
    3. The transaction was included in a block.
    4. The transaction or one of its unconfirmed ancestors conflicts with a transaction that was included in a block.
### 5. Consensus
    All the decisions in a Blockchain network are made using consensus. It helps reach the conclusion as to which transactions are valid and which are not. It is like a voting process. It allows establishing trust between users who cannot communicate directly and effectively. The use case of this concept is best explained through the Byzantine Generals Problem
    
 **Proof of Work**

    The idea of consensus is implied through algorithms and the first one of such a kind to be used was the Proof of Work algorithm used in the Bitcoin network. The idea behind proof of work is that whoever puts in the most work to contribute to the system is the most trustworthy. 

    In Bitcoin, special users called miners perform work of calculating complex mathematical operations to generate required nonce values that have specific constraints put by the system, to validate a block of transaction. As a result of this time and resources of the miner are consumed and for their work they are a paid a fee (reward). This is the only way of creating new coins in  Bitcoin.

    Every block to be mined has a difficulty associated with it in regard to the specific number of zeroes required at the beginning of the hash value. The miners try to guess the nonce value over and over again so that the hash generated matches the required constraints.
    
    In the blockchain, the difficulty of Blocks is adjusted so that only one block is generated every 10 minutes.

    The issues related with PoW algorithm
    1. High Energy consumption
    2. A few select miners with better computational power may obtain mining monopoly mostly in cases of mining pools
    
    A mining pool is a group of miners who pool their resources together to mine blocks and then share their rewards with the members

**Proof of Stake**

    Proof of stake is another algorithm used to help achieve consensus on a blockchain. The key idea behind proof of stake is that it focuses on giving votes to members, depending on how much stake they have in the success of the chain.

    Miners are replaced by validators. They are not required to buy costly mining equipment. Rather be eligible for validating blocks they need to own a stake in the system that will prove that they are trustworthy and will bring positive outcome through participation. Because why would otherwise a person invest so much in a system they wish to break?

    Thus to participate in the process they place their own stakes on the line. If they validate a fraudulent. 

    A possiblke attack on the PoS system is known as Nothing at Stake attack. It expolits the possibilty of having mutliple forks in the blockchain while an update is suggested, they will simply bet on all the possible forks and try and come out on top. To prevent this validators are penalsed if they place bets on multiple chains. this puts validators on a cautious stance. 

    Prime users of PoS are Ethereum, LISK (uses Delegated PoS - top 100 people are stakeholders and they too are voted) and DASH
    
**Delegated Byznatine Fault Tolerance**
    
    Unlike proof of work or proof of stake, DBFT tries to achieve consensus by assigning roles to nodes to help coordinate consensus. 

    So instead of haivng miners it categorizes it's nodes into ordinary or consensus nodes which decide which block is to be added to the network. They work as representative of other ordinary nodes.
    Depending on some criteria put up by the network, consensus nodes are selected. 
    
    The node which suggests a new block for validation is called a speaker and is selcted randomly from the delegates. It requires atleast 2/3rd of the delegate/consensus nodes to agree on it's validation.

    It is faster than PoS or PoW and allows no forking and no cryptographic complex mathematical operation as well. But there is always the issue of malicious delegate or speaker. 
    
    Major users fof DBFT is Neo