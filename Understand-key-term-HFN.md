# Hyperledger-Fabric-Network-Go-Lang-(Understand-HFN)
#### Acknowledgements
- This Github repo, is prepared as a part of Blockchain Setup Lab (Blockchain Honor-Minor Degree Course / Semester 7 Lab) offered by Department of Computer Engineering to the Final year students of VES Institute of Technology, Mumbai (An Autonomous Institute, Affiliated with the University of Mumbai)) during the Academic Year 2025-26.
- This content is prepared on the basis of the Course offered by [Kerala Blockchain Academy (KBA)](https://kba.ai/) : [Hyperledger Fabric Fundamentals (Go Lang)](https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/) 

## **Learning Objectives** : 
1. To understand the [hardware pre-requisites for setting up a Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-0--hardware-prerequisites)
2. To take a walkthrough the [insallation of Packages](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-1--insallation-of-packages)
3. To [bootstraping the Hyperledger Fabric Network using IBM Microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-2--bootstraping-the-network-using-ibm-microfab)
4. To [understand the key terminologies in Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md#objective---4--understanding-key-terminologies-in-hyperledger-fabric-network)
5. To [understand the Use-case scenario - Tracing mangoes](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md#objective---5--use-case-scenario--to-trace-mangoes)
6. To [set up a small Multi-org based Hyperledger Fabric Network in Go Lang](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Setup-HFN.md#objective---6--setting-up-the-hyperledger-fabric-network)  

## Objective - 4 : Understanding Key Terminologies in Hyperledger Fabric Network
1. **Asset** : any given entity that we transfer during a transaction.
2. **Transaction** : an exchange of goods or services between two individuals. It consists of an asset, a set of participants, and the logic of that transaction. 
3. **State** : current condition of a given asset.
4. **Ledger** : the immutable storage of transactions as records as well as saving the current state of an asset.
5. **World State** : used for keeping the state. Implemented using LevelDB / CouchDB which stores data as key-value pairs. (Hyperledger Fabric uses LevelDB).
6. **Smart Contract** : the code that defines the agreements or rules of a transaction.
7. **Chaincode** : a group of similar Smart Contracts. It encapsulates Smart Contracts into a single unit.

**Fabric Contract API** in Golang 
- essential tool for developers for building applications on top of the Hyperledger Fabric
- provides a set of functions to interact with the blockchain network.
- provides a convenient and secure way to write and deploy chaincode on the Fabric network.
- Commonly used methods:
  1. PutState : to create an asset in the Fabric ledger.
  2. GetState : to retrieve an already stored state variable from the ledger.
  3. DeleteState : to remove the asset.

**Lifecycle of a Chaincode**

1. Package the chaincode
2. Install the chaincode on the peers
3. Approve the chaincode definition
4. Commit the chaincode definition

## Objective - 5 : Use-Case Scenario : To trace mangoes 
- **Organizations** : PRODUCER and SELLER.
- **Channel** : Mango Channel
- **Asset** : mango (transferred from PRODUCER to SELLER).
  - attributes of Mango : ID, batchNumber, producer, ownedBy (default = producer), price, quantity.
- **Chain** : MangoChain (records all transactions in ledger)
- **Functions**: 
  1. Create-mango : To set asset properties : ID, batchNumber, producer, ownedBy, price, and quantity.
  2. Exist-mango : To check the existence of the mango by providing the ID  (to avoid the duplication of records).
  3. Read-mango : To view mango details.
  4. Update-mango : To update mango details.
  5. Delete-mango : To delete the mango details from the state.
  6. Sell-mango : To sell mango (change the ownership to the buyer).

**Note** : Transactions are visible only to the participating organizations : PRODUCER and SELLER.
  
![Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Network.png)

## Objective - 6 : [Setting Up the Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Setup-HFN.md#objective---6--setting-up-the-hyperledger-fabric-network)
