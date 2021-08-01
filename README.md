# Blockchain Homework

This project requires to creat a private testnet blockchain for Zbank unsing a Proof of Autgority (PoA) Algorithm 

## Create de Nodes, generate the keys, and inititialized the nodes.
We will generate two nodes with new accounts that will serve as our pre-approved sealer addresses. 
Navigate to the folder in the terminal were the geth tools were installed:\
 `$  cd Desktop/Fintech/BlokchainHomework5`

  and run the following commands:
 
`./geth --datadir node1 account new`\
password: 1234\
Public Key: *0x68Ddf56d22e583Ad5104dcb27f9adf4f0AEf64f5*

Path of the secret key file: node1/keystore/UTC--2021-07-25T15-57-57.025581000Z--68ddf56d22e583ad5104dcb27f9adf4f0aef64f5

`./geth --datadir node2 account new`\

password: 1234\
Public  key: *0xEF80b418c5d4073Ca33F01C6aB9fe3cc660d9c4b*

Path of the secret key file: node2/keystore/UTC--2021-07-25T15-58-16.206742000Z--ef80b418c5d4073ca33f01c6ab9fe3cc660d9c4b


## Generate the genesis Block

Run `./puppeth` and name the network *zbankpoa*
then select options 2, 1 to configure a new genesis and create it from scracht
 Select 2, clique consensus engine, the Block Time:180, chain/network ID:325
 . The new genesis Block is now configured.

 ## Starting the chain

 With the genesis block creation completed, we will now initialize de nodes with the json file

 Using geth, initialize each node with the new networkname.jso\
 `./geth --datadir node1 init zbanchain.json`\
 `./geth --datadir node2 init zbanchain.json`

At this point both nodes are intitialized and can begin mining blocks.
To start the blockchian run the folowing commands in separate terminal windows, in the command for node 1 include the sealer address excluiding the 0x prefix. In the command to start node 2 include the sealer address for node 2 exlcuidng as well th 0x prefix. for the second node  include the enode addrress from node 1

Node1

`./geth --datadir node1 --unlock "68Ddf56d22e583Ad5104dcb27f9adf4f0AEf64f5" --mine --miner.threads 1`

*From node1 Mining log, scroll up and copy the enode address*

`enode://baf6334c997ccaeee4c059f5dd05fbf4457dc06ae2183318bad96b8d85078c66dd770c6a8d5dc7c0749a9c92bc4b53659db5317fde3580c81a89a2f7b794b4dc@127.0.0.1:30303`


Node 2

`./geth --datadir node2 --unlock "EF80b418c5d4073Ca33F01C6aB9fe3cc660d9c4b" --port 30304 --http --bootnodes "enode://baf6334c997ccaeee4c059f5dd05fbf4457dc06ae2183318bad96b8d85078c66dd770c6a8d5dc7c0749a9c92bc4b53659db5317fde3580c81a89a2f7b794b4dc@127.0.0.1:30303"  --allow-insecure-unlock --mine --miner.threads 1`

Make sure you enter the password in both cases even is you can't see visually.

The *zabnkchainet* Private PoA blockchain should now be running!!!!
