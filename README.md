# Hyperledger-Fabric-Network-Go-Lang
**Objective** : To understand and build a small Multi-org based Hyperledger Fabric network 

## Step 0 : Hardware Prerequisites
- Operating System: Ubuntu 20.04 or higher
- RAM: 8GB or higher ( Course is tested in an 8GB machine)
- Free disk space: 40 GB
- High-speed internet connectivity

**Note** : If there are any errors detected, please run the commands suggested.

## Step 1 : Insallation of pakcages

On the Terminal of Ubuntu 20.04 LTS
- $ pwd
- $ cd Desktop
- $ mkdir Blockchain_HFN
- $ cd Blockchain_HFN
- $ sudo apt-get update

#### 1. curl
- Run the command to install Curl : **$ sudo apt-get install curl**
- Verify the installation and check the version of Curl : **$ curl --version**
  
![curl-version]()
  
#### 2. NodeJS
- Remove old version : **$ sudo apt-get remove nodejs | sudo apt-get autoremove**
- Run the command to download and execute the nodejs file : **$ curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -**
- Start the installation for NodeJs :
  **$ sudo apt-get install -y nodejs**
  OR
  **sudo apt install nodejs**
- Check the version of nodejs : **$ node --version OR node -v**

#### 3. vscode

#### 4. build-essentials
- Run the command : **sudo apt install build-essential**



# Acknowledgements
Prepared on the basis of the Course offered by [Kerala Blockchain Academy (KBA)](https://kba.ai/) : [Hyperledger Fabric Fundamentals (Go Lang)](https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/) for the Final year students to experiment on Hyperledger Faric Network in Go Language.
