Source : 
1. https://docs.google.com/document/d/1-Yc8shZdpqEk4nMUwW9gfDwBm3KCZIHZzGKPOZvcQQw/edit?tab=t.0
2. https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/lessons/installing-the-prerequisites-copy/

# Hyperledger-Fabric-Network-Go-Lang
#### Acknowledgements
This Github repo, is prepared as a part of Blockchain Setup Lab (Blockchain Honor-Minor Degree Course / Semester 7 Lab) offered by Department of Computer Engineering to the Final year students of VES Institute of Technology, Mumbai (An Autonomous Institute, Affiliated with the University of Mumbai)) during the Academic Year 2025-26. The content is prepared on the basis of the Course offered by [Kerala Blockchain Academy (KBA)](https://kba.ai/) : [Hyperledger Fabric Fundamentals (Go Lang)](https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/) 

## **Objective** : 
- To understand and build a small Multi-org based Hyperledger Fabric network in Go Lang
## Contents
0. [Hardware Pre-requisites](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-0--hardware-prerequisites)
1. [Insallation of Packages](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-1--insallation-of-packages)
2. [Bootstraping the Network using IBM Microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-2--bootstraping-the-network-using-ibm-microfab)
3. [Understanding Key Terminologies](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-3--understanding-key-terminologies)
4. [Use-Case Scenario : To trace mangoes](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-4-use-case-scenario--to-trace-mangoes)

## Step 0 : Hardware Prerequisites
- Operating System: Ubuntu 24.04 or higher
- RAM: 8GB or higher ( Course is tested in an 8GB machine)
- Free disk space: 40 GB
- High-speed internet connectivity

=============================
[Download Latest version of Ubuntu](https://ubuntu.com/download/desktop)

[Install Ubuntu 24.04 LTS](https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/)

Install Using qemu (simplest CLI-based method)
```
sudo apt update
sudo apt install qemu-system-x86
qemu-system-x86_64 \
  -boot d \
  -cdrom /home/student/Downloads/ubuntu-24.04-desktop-amd64.iso \
  -m 4096 \
  -enable-kvm \
  -cpu host \
  -smp 2 \
  -hda ubuntu24.qcow2
```
==============================

**Note** : If there are any errors detected, please run the commands suggested on the terminal for troubleshooting.

## Step 1 : Insallation of Packages
1. [curl](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#1-curl)
2. [NodeJS](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#2-nodejs)
3. [VScode](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#3-vscode)
4. [build-essentials](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#4-build-essentials)
5. [WEFT Library](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#5-install-weft-library-using-npm)
6. [Docker Community Edition](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#6-install-docker-ce-community-edition-)
7. [Docker Compose](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#7-install-docker-compose)
8. [Go compiler](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#8-go-language-installation)
9. [Add user to the Docker group](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#9-add-user-to-the-docker-group)

On the Terminal of Ubuntu 20.04 LTS
- Current working directory : ```pwd```
- Change the directory : ```cd Desktop```
- List the files in directory : ```ls```
- Create a new folder : ```mkdir Blockchain_HFN```
- Change to the bew folder : ```cd Blockchain_HFN```
- Update the packages list : ```sudo apt-get update```

![folder](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/folder.png)  

Note : If there is an error while executing the above update command, 
- To list all the lock files : ```ps aux | grep -E 'apt|dpkg|apt-get'```
- To teminate all the process which are stuck :
  
  ```
  sudo fuser -vik -TERM /var/lib/dpkg/lock /var/lib/dpkg/lock-frontend /var/lib/apt/lists/lock
  ```

#### 1. curl
- Run the command to install Curl : ```sudo apt-get install curl```
  
![curl-version](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/curl-1.png)

- Verify the installation and check the version of Curl : ```curl --version```

![curl](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/curl-2.png)
  
#### 2. NodeJS
- Remove old version : ```sudo apt-get remove nodejs | sudo apt-get autoremove```
  
- Run the command to download and execute the nodejs file :

  ```curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -```

![nodejs-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/nodejs-1.png)

- Start the installation for NodeJs :

  ```sudo apt-get install -y nodejs```
  OR
  ```sudo apt install nodejs```

![nodejs-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/nodejs-2.png)

- Check the version of nodejs :
  ```node --version```
  OR
  ```node -v```

![nodejs-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/nodejs-3.png)

- Check the version of npm : ```npm -v```

![npm-version](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/npm-version.png)
  

#### 3. vscode
- Install dependencies :

  ```sudo apt install software-properties-common apt-transport-https wget```
  
- Import Microsoft GPG key :

  ```wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -```
  
- Add the VS Code repository :

  ```sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"```
  
![vscode-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/vscode-install.png)

- Update package lists again : ```sudo apt update```
- Install VS Code : ```sudo apt install code```

![vscode-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/vscode-install2.png)

- Check the version : ```code -v```

![vscode-install](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/vscode-instll-3.png)

#### 4. build-essentials
- Run the command : ```sudo apt install build-essential```

![build](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/build.png)

#### 5. Install WEFT Library using npm
``` curl -sSL https://raw.githubusercontent.com/hyperledger-labs/weft/main/install.sh | sh```

OR

```sudo npm install -g @hyperledgendary/weftility ```

![weft](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/weft.png)

#### 6. Install Docker CE (Community Edition )
- Remove old versions of docker :

  ```sudo apt-get remove docker docker-engine docker.io containerd runc```
  
- Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```sudo apt-get update```

```
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

- Add Docker’s official GPG key:

```curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg```

- Set up the stable repository:

  ```
  echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```

- Update the apt package index, and install the latest version of Docker CE:

  ```sudo apt-get update```
  
  ```sudo apt-get install docker-ce docker-ce-cli containerd.io```

- Verify that Docker CE is installed correctly:
  
  ```sudo docker run hello-world```

![hello](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/docker-hello.png)

- Check the version of Docker : ```docker --version```

![docker-version](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/docker-version.png)

#### 7. Install Docker Compose
- Download the current stable release of Docker Compose:

```sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose```

- Apply executable permissions to the binary:

 ```sudo chmod +x /usr/local/bin/docker-compose```

- Check the version : ```docker-compose --version```

![docker-compose](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/docker-compose.png)

#### 8. Go Language Installation
- Download Go :

  ```wget https://golang.org/dl/go1.17.6.linux-amd64.tar.gz```
  
- Extract the archive :

  ```sudo tar -xvf go1.17.6.linux-amd64.tar.gz```
  
- Move the Go binary files to /usr/local :

```sudo mv go /usr/local```

- Add Go binary path to the system PATH :

  ```echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.profile```

  ```source ~/.profile```

- Verify Go installation : ```go version```

![go-version](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/go-version.png)

#### 9. Add user to the Docker group
- [Source : How to fix the permission denied error in Docker](https://www.hostinger.com/in/tutorials/how-to-fix-docker-permission-denied-error?utm_campaign=Generic-Tutorials-DSA|NT:Se|LO:IN-t2&utm_medium=ppc&gad_source=1&gad_campaignid=18585456941&gclid=CjwKCAjwqKzEBhANEiwAeQaPVeT-1umqXqnV0eS0d488_XewDerLLVviCI1kHjxQt_hrGfAU4-fg9hoCwnEQAvD_BwE)

**Note** : 
- By default, Docker runs as a root-owned service. To manage Docker as a non-root user, your user needs to be part of the docker group. This allows you to run Docker commands without needing sudo.
1. To add user to docker group: ```sudo usermod -aG docker $USER```
  - This command appends your user to the docker group, allowing permission to access the Docker daemon files and directories.
2. Log in to a new group: ```newgrp docker```
3. Check if your user has docker group membership : ```groups```
4. Run the docker command : ```docker ps``` to list all the containers without needing root privileges.

## Step 2 : Bootstraping the Network using IBM Microfab
Microfab is a containerized Hyperledger Fabric runtime for use in development environments.

#### 1. For running the network, copy the below export command and execute it in a command terminal

```
export MICROFAB_CONFIG='{
"port": 8080,
"endorsing_organizations":[
{
"name": "ProducersOrg"
},
{
"name": "SellersOrg"
}
],
"channels":[
{
"name": "mango-channel",
"endorsing_organizations":[
"ProducersOrg",
"SellersOrg"
]
}
]
}'
```

- port: Port on which Microfab container is mapped to run. This configuration file is in JSON format a key-value format.
- endorsing_organisations: Organisations present in a business network.
- channels: Name of the channel on which the network is operated.

![Config](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/config.png)

#### 2. Execute the following command:
- To run the runtime docker environment :

  ```docker run -e MICROFAB_CONFIG -p 8080:8080 ibmcom/ibp-microfab```

![run-microfab-docker](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab.png)

![microfab-0](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab-0.png)

![microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab-1.png)

![run-microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab-2.png)

![run-microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab-3.png)
  
- To stop the container : Press ```Control + C```

![stop](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/docker-stop.png)
  
- To remove the container : ```docker container prune```

![docker-prune](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/docker-prune.png)

## Step 3 : Understanding Key Terminologies
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

## Step 4. Use-Case Scenario : To trace mangoes 
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

## Step 5. Setting Up the Project
### Terminal-1 : Run the Network
**1. Copy the below export command and execute it in a command terminal**

```
export MICROFAB_CONFIG='{
"port": 8080,
"endorsing_organizations":[
{
"name": "ProducersOrg"
},
{
"name": "SellersOrg"
}
],
"channels":[
{
"name": "mango-channel",
"endorsing_organizations":[
"ProducersOrg",
"SellersOrg"
]
}
]
}'
```
![Config](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/config.png)

**2. Run the runtime docker environment :**

  ```docker run -e MICROFAB_CONFIG -p 8080:8080 ibmcom/ibp-microfab```

![run-microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/run-microfab-3.png)

### Terminal-2 : Run the Project
**1. Create a folder :**  ```mkdir HFN-Mango```

**2. Change the directory :** ```cd HFN-Mango```

**3. Generate Certificates, wallet and gateway connection profile :**

```
curl -s http://console.127-0-0-1.nip.io:8080/ak/api/v1/components | weft microfab -w ./_wallets -p ./_gateways -m ./_msp -f
```
Note : If there is an error in this command w.r.t weft utility, rerun the code at [Step 5 under Installation](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#5-install-weft-library-using-npm)

![ca](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/folder-hfn-mango.png)

![ca](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/ca-wallet-gateway-0.png)

![ca](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/ca-wallet-gateway-2.png)

**Alert :** Environment variables will be different in path settings 
- For producersorgadmin @  ProducersOrg use these:
```
export CORE_PEER_LOCALMSPID=ProducersOrgMSP
export CORE_PEER_MSPCONFIGPATH=/home/lifna/Desktop/Blockchain-HFN/HFN-Mango/_msp/ProducersOrg/producersorgadmin/msp
export CORE_PEER_ADDRESS=producersorgpeer-api.127-0-0-1.nip.io:8080
```

- For producersorgcaadmin @  ProducersOrg use these:
```
export CORE_PEER_LOCALMSPID=ProducersOrgMSP
export CORE_PEER_MSPCONFIGPATH=/home/lifna/Desktop/Blockchain-HFN/HFN-Mango/_msp/ProducersOrg/producersorgcaadmin/msp
export CORE_PEER_ADDRESS=producersorgpeer-api.127-0-0-1.nip.io:8080
```

- For sellersorgadmin @  SellersOrg use these:
```
export CORE_PEER_LOCALMSPID=SellersOrgMSP
export CORE_PEER_MSPCONFIGPATH=/home/lifna/Desktop/Blockchain-HFN/HFN-Mango/_msp/SellersOrg/sellersorgadmin/msp
export CORE_PEER_ADDRESS=sellersorgpeer-api.127-0-0-1.nip.io:8080
```

- For sellersorgcaadmin @  SellersOrg use these:
```
export CORE_PEER_LOCALMSPID=SellersOrgMSP
export CORE_PEER_MSPCONFIGPATH=/home/lifna/Desktop/Blockchain-HFN/HFN-Mango/_msp/SellersOrg/sellersorgcaadmin/msp
export CORE_PEER_ADDRESS=sellersorgpeer-api.127-0-0-1.nip.io:8080
```

**4. Set the environment variables for Producer & Seller Organization**
- Copy the export commands above and execute them in the terminal.

![pro-cmd](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/path-setting.png)
   
**5. Install Binaries for handling Chaincode Lifecycle**
```
curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh | bash -s -- binary
```

![binary-1](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/binary-1.png)

![binary-2](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/binary-2.png)

**6. Add the path of the bin and config folders to the environment variables.**
```
export PATH=$PATH:${PWD}/bin
export FABRIC_CFG_PATH=${PWD}/config
```
![path](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/path.png)

### Open the HFN-Mango Project in VSCode

![prjt-open](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/vs-1.png)

**1. Create a folder for chaincode : HFN-Mango-Contract**

**2. Open the terminal** 
- Change the directory : ```cd HFN-Mango-Contract```
- Initialize the Project : ```go mod init mango```
  - This will create a **go.mod** file inside the HFN-Mango-Contract folder, where the project dependencies and its version details will be mentioned.\

**3. Create smart contract in the folder HFN-MAngo-Contract**
- File : **mangoContract.go** (To define the business logic)
```
package main

import (
   "encoding/json"
   "fmt"
   "github.com/hyperledger/fabric-contract-api-go/contractapi"
)

type MangoContract struct {
   contractapi.Contract
}
type Mango struct {
   ID          string  `json:"ID"`
   BatchNumber int     `json:"BatchNumber"`
   Producer    string  `json:"Producer"`
   OwnedBy     string  `json:"OwnedBy"`
   Quantity    int     `json:"Quantity"`
   Price       float32 `json:"Price"`
}

// MangoExists returns true when asset with given ID exists in world state
func (c *MangoContract) MangoExists(ctx contractapi.TransactionContextInterface, mangoID string) (bool, error) {
   data, err := ctx.GetStub().GetState(mangoID)
   if err != nil {
       return false, err
   }
   return data != nil, nil
}

// CreateMango creates a new instance of Mango
func (c *MangoContract) CreateMango(ctx contractapi.TransactionContextInterface, mangoID string, batchNumber int,
   producer string, quantity int, price float32) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if exists {
       return fmt.Errorf("The asset %s already exists", mangoID)
   }
   mango := Mango{
       ID:          mangoID,
       BatchNumber: batchNumber,
       Producer:    producer,
       OwnedBy:     producer,
       Quantity:    quantity,
       Price:       price,
   }
   bytes, _ := json.Marshal(mango)
   return ctx.GetStub().PutState(mangoID, bytes)
}

// ReadMango retrieves an instance of Mango from the world state
func (c *MangoContract) ReadMango(ctx contractapi.TransactionContextInterface, mangoID string) (*Mango, error) {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return nil, fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return nil, fmt.Errorf("The asset %s does not exist", mangoID)
   }
   bytes, _ := ctx.GetStub().GetState(mangoID)
   mango := new(Mango)
   err = json.Unmarshal(bytes, mango)
   if err != nil {
       return nil, fmt.Errorf("Could not unmarshal world state data to type Mango")
   }
   return mango, nil
}

// UpdateMango retrieves an instance of Mango from the world state and updates its value
func (c *MangoContract) UpdateMango(ctx contractapi.TransactionContextInterface, mangoID string, batchNumber int, producer string, owner string, quantity int, price float32) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return fmt.Errorf("The asset %s does not exist", mangoID)
   }
   mango := Mango{
       ID:          mangoID,
       BatchNumber: batchNumber,
       Producer:    producer,
       OwnedBy:     owner,
       Quantity:    quantity,
       Price:       price,
   }
   bytes, _ := json.Marshal(mango)
   return ctx.GetStub().PutState(mangoID, bytes)
}

// DeleteMango deletes an instance of Mango from the world state
func (c *MangoContract) DeleteMango(ctx contractapi.TransactionContextInterface, mangoID string) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return fmt.Errorf("The asset %s does not exist", mangoID)
   }
   return ctx.GetStub().DelState(mangoID)
}

func main() {
   mangoContract := new(MangoContract)
   chaincode, err := contractapi.NewChaincode(mangoContract)
   if err != nil {
       panic("Could not create chaincode." + err.Error())
   }
   err = chaincode.Start()
   if err != nil {
       panic("Failed to start chaincode. " + err.Error())
   }
}
``` 

**4. Install all the required external packages**
- To fetch the github repo for Hyperledger Fabric Contract API :

```go get github.com/hyperledger/fabric-contract-api-go@v1.2.1```

- This command adds all the external packages to **go.mod** file and generates **go.sum** file in the folder

```go mod tidy```

![go-tidy](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/go-tidy.png)

- Updations made to **go.mod** file

![go-mod](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/go-mod.png)

- Contents of **go.sum** file

![go-sum](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/go-sum.png)


### Deploy the chaincode on the Terminal-2

**1. Package the chaincode :**

- It is the process of wrapping up the smart contracts in the folder into a packaged chaincode and generate the **tar.gz** file

```peer lifecycle chaincode package mango.tgz --path ./HFN-Mango-Contract/ --lang golang --label mango_1```

**2. Install the chaincode :**

- Run the command :

```peer lifecycle chaincode install mango.tgz```

- Output : 2024-07-16 15:09:00.553 IST 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nHmango_1:8ebd38bffcf4c843359402af81071b74b321e870304effa088c257ecc7d11c8d\022\007mango_1" > 
2024-07-16 15:09:00.553 IST 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: mango_1:8ebd38bffcf4c843359402af81071b74b321e870304effa088c257ecc7d11c8d
  
- Copy the chaincode package identifier starting with ‘mango’ and export it as follows:

```export CC_PACKAGE_ID=mango_1:**8ebd38bffcf4c843359402af81071b74b321e870304effa088c257ecc7d11c8d**```

- **Note :** The package identifier generated may be different, edit it accordingly and export

**3. Approve the Chaincode**

- This stage ensures that all participating organizations agree on the version and content of the chaincode.
- Execute the below command to approve the chaincode
  
```
peer lifecycle chaincode approveformyorg -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel --name mango --version 1 --sequence 1 --waitForEvent --package-id ${CC_PACKAGE_ID}
```
- Output : 2024-07-16 15:11:30.330 IST 0001 INFO [chaincodeCmd] ClientWait -> txid [82c929e58ea0681f9b3fee4e42c8eaeb38724b6b4a0b223c2234c7b0e2dd313b] committed with status (VALID) at producersorgpeer-api.127-0-0-1.nip.io:8080


**4. Commit the Chaincode**

- This stage ensures that the approved chaincode being added to the channel by the endorsing organization, after which it can be invoked by applications on the channel.
- Execute the below command to commit the chaincode

```
peer lifecycle chaincode commit -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel --name mango --version 1 --sequence 1
```
- Output : 2024-07-16 15:14:39.450 IST 0001 INFO [chaincodeCmd] ClientWait -> txid [a61bb6ea896ecf9a46907185e3ba9fd99c970998a758d7535b085ba92b234b78] committed with status (VALID) at producersorgpeer-api.127-0-0-1.nip.io:8080


### Perform the Transactions

**1. Invoke a transaction** : to update the ledger
- That is to change the data that is associated with an asset.

![tx-flow](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/tx-flow.png)

**Create an asset**
a. CreateMango
  
```
peer chaincode invoke -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"CreateMango","Args":["MANGO1","1","mango corp","5000","10000"]}'
```
- Output : 2024-07-16 15:17:33.255 IST 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200
   
```
peer chaincode invoke -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"CreateMango","Args":["MANGO2","2","ibm corp","50","1000"]}'
```
- Output : 2024-07-16 15:19:38.637 IST 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200

b. UpdateMango
```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"UpdateMango","Args":["MANGO2","2","ibm corp","asmi","50","1000"]}'
```

c. DeleteMango
```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"DeleteMango","Args":["MANGO2"]}'
```

**2. Query** : to retrieve information. 
- There is no data alteration, and it is not recorded in the ledger
- The data will be retrieved from any of the peers and sent back to the client.
 
![query-1](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/query-1.png)

![query-2](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/query-2.png)

**Retrieve an asset**
a. ReadMango

```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"ReadMango","Args":["MANGO1"]}'
```
- Outpu : {"ID":"MANGO1","BatchNumber":1,"Producer":"mango corp","OwnedBy":"mango corp","Quantity":5000,"Price":10000}

```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"ReadMango","Args":["MANGO2"]}'
```
- Output : {"ID":"MANGO2","BatchNumber":2,"Producer":"ibm corp","OwnedBy":"ibm corp","Quantity":50,"Price":1000}

b. MangoExists

```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"MangoExists","Args":["MANGO2"]}'
```
- Output : true

```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"MangoExists","Args":["MANGO1"]}'
```
- Output : true

### Update the Chaincode

- To upgrade the chaincode with more functionalities
- Add the following code snippet to the mangoContract.go file 
- **SellMango** : transfer the asset’s ownership status (mango) to the new owner. The three arguments : mango Id, current owner, and new owner.
- Updated chaincode is as follows:
  
```
package main

import (
   "encoding/json"
   "fmt"
   "github.com/hyperledger/fabric-contract-api-go/contractapi"
)

type MangoContract struct {
   contractapi.Contract
}
type Mango struct {
   ID          string  `json:"ID"`
   BatchNumber int     `json:"BatchNumber"`
   Producer    string  `json:"Producer"`
   OwnedBy     string  `json:"OwnedBy"`
   Quantity    int     `json:"Quantity"`
   Price       float32 `json:"Price"`
}

// MangoExists returns true when asset with given ID exists in world state
func (c *MangoContract) MangoExists(ctx contractapi.TransactionContextInterface, mangoID string) (bool, error) {
   data, err := ctx.GetStub().GetState(mangoID)
   if err != nil {
       return false, err
   }
   return data != nil, nil
}

// CreateMango creates a new instance of Mango
func (c *MangoContract) CreateMango(ctx contractapi.TransactionContextInterface, mangoID string, batchNumber int,
   producer string, quantity int, price float32) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if exists {
       return fmt.Errorf("The asset %s already exists", mangoID)
   }
   mango := Mango{
       ID:          mangoID,
       BatchNumber: batchNumber,
       Producer:    producer,
       OwnedBy:     producer,
       Quantity:    quantity,
       Price:       price,
   }
   bytes, _ := json.Marshal(mango)
   return ctx.GetStub().PutState(mangoID, bytes)
}

// ReadMango retrieves an instance of Mango from the world state
func (c *MangoContract) ReadMango(ctx contractapi.TransactionContextInterface, mangoID string) (*Mango, error) {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return nil, fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return nil, fmt.Errorf("The asset %s does not exist", mangoID)
   }
   bytes, _ := ctx.GetStub().GetState(mangoID)
   mango := new(Mango)
   err = json.Unmarshal(bytes, mango)
   if err != nil {
       return nil, fmt.Errorf("Could not unmarshal world state data to type Mango")
   }
   return mango, nil
}

// UpdateMango retrieves an instance of Mango from the world state and updates its value
func (c *MangoContract) UpdateMango(ctx contractapi.TransactionContextInterface, mangoID string, batchNumber int, producer string, owner string, quantity int, price float32) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return fmt.Errorf("The asset %s does not exist", mangoID)
   }
   mango := Mango{
       ID:          mangoID,
       BatchNumber: batchNumber,
       Producer:    producer,
       OwnedBy:     owner,
       Quantity:    quantity,
       Price:       price,
   }
   bytes, _ := json.Marshal(mango)
   return ctx.GetStub().PutState(mangoID, bytes)
}

// DeleteMango deletes an instance of Mango from the world state
func (c *MangoContract) DeleteMango(ctx contractapi.TransactionContextInterface, mangoID string) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return fmt.Errorf("The asset %s does not exist", mangoID)
   }
   return ctx.GetStub().DelState(mangoID)
}

func (c *MangoContract) SellMango(ctx contractapi.TransactionContextInterface, mangoID string,
   owner string, newOwner string) error {
   exists, err := c.MangoExists(ctx, mangoID)
   if err != nil {
       return fmt.Errorf("Could not read from world state. %s", err)
   } else if !exists {
       return fmt.Errorf("The asset %s does not exist", mangoID)
   }
   mango, _ := c.ReadMango(ctx, mangoID)
   if mango.OwnedBy == owner {
       mango.OwnedBy = newOwner
       bytes, _ := json.Marshal(mango)
       return ctx.GetStub().PutState(mangoID, bytes)
   }else{
       return fmt.Errorf("Assset is not owned by %v, only original owner can sell the asset", owner)
   }
      
}

func main() {
   mangoContract := new(MangoContract)
   chaincode, err := contractapi.NewChaincode(mangoContract)
   if err != nil {
       panic("Could not create chaincode." + err.Error())
   }
   err = chaincode.Start()
   if err != nil {
       panic("Failed to start chaincode. " + err.Error())
   }
}
```

### Steps for redeploying the chaincode

**1. Package the chaincode.**
```
peer lifecycle chaincode package mango.tgz --path ./KBA-Mango-Contract/ --lang golang --label mango_2
```
**Note** : Change the label --> mango_2 in order to distinguish the previous and new chaincode.

**2. Install the chaincode:**
```
peer lifecycle chaincode install mango.tgz
```
- Output : 2024-07-16 15:37:28.719 IST 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nHmango_2:706ec13f71ec584ef71a2c5a601718e25ea1cf197037fbb04c2b80780c6bfeb7\022\007mango_2" > 
2024-07-16 15:37:28.719 IST 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: mango_2:706ec13f71ec584ef71a2c5a601718e25ea1cf197037fbb04c2b80780c6bfeb7

**Note** : This command generates a new chaincode package id starting with ‘mango’. Export it as an environment variable.

```
export CC_PACKAGE_ID=mango_2:706ec13f71ec584ef71a2c5a601718e25ea1cf197037fbb04c2b80780c6bfeb7
```

**3. Approve the chaincode :**
```
peer lifecycle chaincode approveformyorg -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel --name mango --version 2 --sequence 2 --waitForEvent --package-id ${CC_PACKAGE_ID}
```
- Output : 2024-07-16 15:39:08.603 IST 0001 INFO [chaincodeCmd] ClientWait -> txid [fa848034acf8252a62782a3b73157fc6b4bfeec1177e9f1fa4a9e7b01d27d906] committed with status (VALID) at producersorgpeer-api.127-0-0-1.nip.io:8080

**Note:** Change the sequence and version here to distinguish between the previous chaincode and the upgraded chaincode. 

**4. Commit the chaincode:**
```
peer lifecycle chaincode commit -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel --name mango --version 2 --sequence 2
```
- Output : 2024-07-16 15:40:30.872 IST 0001 INFO [chaincodeCmd] ClientWait -> txid [0ba504f5734825d9a57afd7b79c1d9f7e1eb6b0419fa775706a49fe1da77f2a0] committed with status (VALID) at producersorgpeer-api.127-0-0-1.nip.io:8080

**5. Invoke the SellMango function** to sell the mango from “mango corp” to “mango shop”
```
peer chaincode invoke -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"SellMango","Args":["MANGO1","mango corp","mango shop"]}'
```
- Output : 2024-07-16 15:41:46.780 IST 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200

**6. Invoke the  ReadMango function** to check the owner of mango.
```
peer chaincode query  -o orderer-api.127-0-0-1.nip.io:8080 --channelID mango-channel -n mango -c '{"function":"ReadMango","Args":["MANGO1"]}'
```
- Output : {"ID":"MANGO1","BatchNumber":1,"Producer":"mango corp","OwnedBy":"mango shop","Quantity":5000,"Price":10000}
