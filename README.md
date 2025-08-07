Source : 
1. https://docs.google.com/document/d/1-Yc8shZdpqEk4nMUwW9gfDwBm3KCZIHZzGKPOZvcQQw/edit?tab=t.0
2. https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/lessons/installing-the-prerequisites-copy/

# Hyperledger-Fabric-Network-Go-Lang
#### Acknowledgements
- This Github repo, is prepared as a part of Blockchain Setup Lab (Blockchain Honor-Minor Degree Course / Semester 7 Lab) offered by Department of Computer Engineering to the Final year students of VES Institute of Technology, Mumbai (An Autonomous Institute, Affiliated with the University of Mumbai)) during the Academic Year 2025-26.
- This content is prepared on the basis of the Course offered by [Kerala Blockchain Academy (KBA)](https://kba.ai/) : [Hyperledger Fabric Fundamentals (Go Lang)](https://learn.kba.ai/course/hyperledger-fabric-fundamentals-golang/) 

## **Objective** : 
1. To understand the [hardware pre-requisites for setting up a Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-0--hardware-prerequisites)
2. To take a walkthrough the [insallation of Packages](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-1--insallation-of-packages)
3. To [bootstraping the Hyperledger Fabric Network using IBM Microfab](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#step-2--bootstraping-the-network-using-ibm-microfab)
4. To [understand the key terminologies in Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md)
5. To [understand the Use-case scenario - Tracing mangoes](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md#objective---5--use-case-scenario--to-trace-mangoes)
6. To [set up a small Multi-org based Hyperledger Fabric Network in Go Lang](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Setup-HFN.md#objective---6--setting-up-the-hyperledger-fabric-network)  

## Objective - 1 : Hardware Prerequisites for setting up a Hyperledger Fabric Network
- Operating System: Ubuntu 24.04 or higher [Steps to upgrade from Ubuntu 20.04 to 24.04 LTS](https://www.tecmint.com/upgrade-ubuntu-20-04-to-24-04/)
- RAM: 8GB or higher ( Course is tested in an 8GB machine)
- Free disk space: 40 GB
- High-speed internet connectivity

**Note** : If there are any errors detected, please run the commands suggested on the terminal for troubleshooting.

## Objective - 2 : Insallation of Packages
1. [curl](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#1-curl)
2. [NodeJS](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#2-nodejs)
3. [VScode](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#3-vscode)
4. [build-essentials](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#4-build-essentials)
5. [WEFT Library](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#5-install-weft-library-using-npm)
6. [Docker Community Edition](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#6-install-docker-ce-community-edition-)
7. [Docker Compose](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#7-install-docker-compose)
8. [Go compiler](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#8-go-language-installation)
9. [Add user to the Docker group](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang#9-add-user-to-the-docker-group)

On the Terminal of Ubuntu 24.04 LTS
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

## Objective - 3 : Bootstraping the Network using IBM Microfab
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

## Objective - 4 : [Understanding Key Terminologies in Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md#objective---4--understanding-key-terminologies-in-hyperledger-fabric-network)

## Objective - 5 : [Use-Case Scenario : To trace mangoes](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Understand-key-term-HFN.md#objective---5--use-case-scenario--to-trace-mangoes)

## Objective - 6 : [Setting Up the Hyperledger Fabric Network](https://github.com/LifnaJos/Hyperledger-Fabric-Network-Go-Lang/blob/main/Setup-HFN.md#objective---6--setting-up-the-hyperledger-fabric-network)
