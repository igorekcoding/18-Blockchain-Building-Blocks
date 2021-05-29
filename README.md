# 18-Blockchain-Building-Blocks
Homework 18
Instructions for DeFi!
I have set up a blockchain testnet for DeFI called DeFi in order to test blockchain functionality. 

Creating the DeFi network
The DeFi network has been set up using puppeth, a helper tool from the geth (Go Ethereum) library for managing private blockchains. Puppeth is saved in the Blockchain-Tools folder. We seeded the network with a genesis block that uses Clique proof-of-authority to add blocks to the blockchain:

Created new network 'DeFi' via ./puppeth:
ChainID: 2052
Proof-of-Authority
Blocktime: every 10 seconds

Creating the network nodes
Using the geth command-line tool, I created the following two nodes on the network which have been initialized with the DeFi genesis block:

node_hw1 Public address of the key: 0xaAEe663C13b6af1d88aF9B9011508D20de447a31

node_hw2 Public address of the key: 0xF7081bdA5D5258dE0a6a066E091bA396Ff30t882

Starting the network
To start the network, in Terminal please navigate to the Blockchain-Tools folder which contains the node data. First start node 1 as a full mining node on the zblock network using the following command:

./geth --datadir node_hw1 --unlock "0xaAEe663C13b6af1d88aF9B9011508D20de447a31" --rpc --mine --miner.threads 1 --ipcdisable --allow-insecure-unlock
This geth command calls node_hw1 in unlocked mode and exposes it to rpc (--rpc: Remote Procedural Call) a network element to facilitate node communication which allows us to use apps like MyCrypto which we'll do below. The node is set up as a mining node with the flags '--mine --miner.threads 1'. The flags '--ipcdisable' and '--allow-insecure-unlock' disable select security features.

After executing the command, wait while the node is initialized and initial output is generated on the screen. After about 30-60 seconds the message 'looking for peers' should appear repeatedly.

Find the output that starts with 'enode://' followed by a hash string and copy this code. You'll use this code to start the second node with this command:

./geth --datadir node_hw2 --unlock "0xF7081bdA5D5258dE0a6a066E091bA396Ff30t882" --port 30304 --bootnodes "enode://CORRECT ENODE ADDRESS HERE" --mine --miner.threads 1 --allow-insecure-unlock --ipcdisable
This geth command starts the second node, node_hw2, also in an unlocked mode. It assigns a subsequent port 30305 as 30306 is already used by the first node. The '--bootnodes' flag stipulates the other nodes that are part of the network via the enode address. This node is also set up as a miner node with the "--mine --miner.threads 1" flags.

After executing the command, similar output will be generated on screen. After about 30-60 seconds the message 'looking for peers' should appear repeatedly.

Sending transactions via MyCrypto
We will use the wallet application MyCrypto to send a test transaction. Open MyCrypto wallet and click on Keystore File to open the first node.

<img width="1154" alt="Screen Shot 2021-05-28 at 7 52 38 PM" src="https://user-images.githubusercontent.com/75813285/120051390-6c001b00-bfee-11eb-927e-510696754550.png">

a) The enter the public address of the second node node_hw2 and the amount of ETH to send (25), then hit Send Transaction and confirm.
b) After confirming the transaction, click on Check TX Status
c)You can check the balance of node_hw1 by logging back in with the keystore file as explained above, and see how the balance has decreased by 25 ETH. Congratulations! You've just sent your first transaction on the blockchain.
