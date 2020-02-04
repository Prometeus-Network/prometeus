
<h1 align="center">
  <br>
  <img src="https://github.com/Prometeus-Network/prometeus/blob/master/docs/diagrams/prom_logo.png" alt="Prometeus" width="160">
  <br>
  Prometeus Network
  <br>
</h1>

<h3 align="center"> Decentralised marketplace for trustless data exchange </h3>
 <br> 
 <br> 

Prometeus Network is a secure and decentralized protocol that allows fully trustless and anonymous data exchange through the use of PROM token. Thus one can say that PROM is like BitCoin for data. This opens a new set of opportunities in the data exchange as well as enriching the transactional side of public blockchain application. 

PROM data exchange protocol allows several use case application scenarios : 
- Exchange any type of data in trustless and private manner( documents, pictures, videos, etc.);
- Serve as a decentralised cross horizontal data exchange hub for big data( prospective markets are Health Care, Finance, Public, Research, Retail, Marketing);
- Perform cross-industry data exchange: Prometeus can connect data providers from any industry to data consumers from any industry;

## Table of contents

- [Features](#license)
- [How it works](#how-it-works)
- [How to test](#how-to-test)
- [Tech stack](#tech-stack)
- [Prometeus nodes](#prometeus-nodes)
    - [Data Mart node](#data-mart-node)
    - [Service node](#service-node)
    - [Data Validator node](#data-validator-node)
- [License](#license)

## Features
Autonomous & Open data exchange controlled by users : Prometeus is open source public blockchain protocol, anyone can take any role in the Prometeus Network, data providers and data consumers control the transactions in a real market form, setting price, privacy & security levels.

Private and censorship resistant - Prometeus protocol operated on a public blockchain and used decentralised storage and ensures selective disclosure of personal and transactional data by the user. 

Quality assurance of data: although Prometeus can not do quality assurance directly, we have built in protocol a transparent and comprehensive rating system that allows new market participants to filter data providers. 

## How it works

Data Owners is the person or the company that have got some valuable data and Data Validator uploads the data to the System. Service Node is intermediate layer between all other actors into the System. If some brand or agency (Data Mart's client) would like to purchase some of that valuable data, they pay to the Data Mart for it. Data Mart purchases PROM tokens at the crypto exchange: that ensures PROM tokens liquidity and demand. When Service Node performs a data delivery, Data Validator grants that Data Owners will be rewarded for their data.

<p align="center">
<img src="https://github.com/Prometeus-Network/prometeus/blob/master/docs/diagrams/Prometeus_scheme_1.png" alt="Prometeus scheme 1">
</p>

The scheme below clearly shows the general procedure of the circulation of the data and PROM tokens within the System.

<img src="https://github.com/Prometeus-Network/prometeus/blob/master/docs/diagrams/Prometeus_scheme_2.png" alt="Prometeus scheme 2">

1. Data Owners share their Valuable Data with Data Validator.
2. Data Validator checks up their data and validate them. Data Validator encrypts the data and upload it to the Data Broker (integral part of Service Node). Service Node stores the data in the Distributed Data Storage. Now the Valuable Data is ready for further purchase.
3. With the passage of time, some end users explored the data and found it interesting. So, they decided to purchase it via Data Mart
4. Data Mart started the purchase process: she wants to buy the Valuable Data for PROM tokens via Service Node.
5. Smart contract distributes PROM tokens among parties to a transaction. 
6. Data Owners are now rewarded for their Valuable Data. 
7. Data Validator already approved the transaction (decryption key granted) so the Service Node will take care about purchased data: retrieve them from Distributed Data Storageand pass them to the Data Mart.
8. Data Mart uses the decryption key and passed the decrypted Valuable Data to the end users.

## How to test

For the testing purposes, you can deploy your instances of system nodes (see install instructions in the appropriate repos) or use the UI of our test nodes, which we implemented in advance for ease of testing and demonstration.

Here is UI of [Data Validator Node](http://178.128.240.29/) and testing [instructions](https://github.com/Prometeus-Network/data-validator-node/blob/master/test.md)

Here is UI of [Data Mart Node](http://178.62.207.53:3008/) and testing [instructions](https://github.com/Prometeus-Network/data-mart-node/blob/master/test.md)

Here is UI of [Prom Blockchain Explorer](http://178.62.211.224/) that allows to explore all the transactions in our tesnet.

## Tech stack

Fork of [Go implementation of the Ethereum protocol](https://github.com/ethereum/go-ethereum): decentralized platform that runs smart contracts, applications that run exactly as programmed without possibility of downtime, censorship, fraud or third party interference.

Ethereum Plasma: an off-chain solution that strives to significantly increase the overall performance of the Ethereum network, by creating a tree-like structure of numerous smaller chains, which would be able to handle more transactions per second.

[Filecoin](https://github.com/filecoin-project/lotus): a decentralized data storage network on top of InterPlanetary File System (IPFS). We use it as a base of our disrtibuted data storage modulem that allows us to store the Data owner's files in most secured and decentralized way.

[Elasticsearch](https://github.com/elastic/elasticsearch): a search engine provides a distributed, multitenant-capable full-text search engine. We use it for caching metadata from the blockchain and that allows Data Mart users to explore the Data Owner's data fast and easy.

## Prometeus nodes

Prometeus Network conists of three types of the nodes:
- Data Validator, which deals with Data Owners and uploads their valuable data to the System
- Data Mart, which enables everybody to explore and buy the valuable data in the System
- Service Node, running the communication service that implements a delivery guarantee: intermediate layer between Data Validators and Data marts.

### Data Validator node 

Data Validator node is an application which is responsible for aggregation and validation of the data from the Data Owners and provide it to Prometeus ecosystem. It provides RESTful API  and user interface for uploading data. The Node uploads data of Data Owners to the Prometeus network using API of Service Node so that it can become available for purchase to Data marts. The payment for the storage of that data is charged at the moment of upload via the smart contract. Besides that, Data Validator Node makes initial encryption of uploaded data using the Data Owner's public key.

Here is a [Data Validator repo](https://github.com/Prometeus-Network/data-validator-node) with more detailed information abouth this Node.

### Data Mart node 

Data Mart node is an application which is used for purchasing data and proceeding it to the buyer (end user: some brand or agency outside the System). It allows to browse metadata (via special UI) and purchase any Data Owners’ data within the System using API of Service Node. Besides that, Data Validator Node makes final decryption of the data.

Here is a [Data Mart repo](https://github.com/Prometeus-Network/data-mart-node) with more detailed information abouth this Node.

### Service node 

Service Node is a distributed application which acts as an intermediate layer between all the Roles within the System. Service Node uses based on private Ethereum network + Ethereum Plasma under the hood: due to the requirement of providing large volumes of information to the clients the quickest way possible. Service Node arranges the storage of encrypted data in a distributed data storage, and metadata in Ethereum blockchain. Upon data uploading Data Validator commits payment which is distributed among Service Nodes via smart contract. Upon data purchasing Data Mart (see below) commits payment which is distributed among Data Validators and Data Owners via smart contract. Part of each purchase payment is kept by Service Node as a commissionary fee.

Here is a [Service node repo](https://github.com/Prometeus-Network/service-node_net) with more detailed information abouth this Node.

## License

Prometeus Network is licensed under the Apache software license (see LICENSE [file](https://github.com/Prometeus-Network/prometeus/blob/master/LICENSE)). Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either \express or implied.

Prometeus Network makes no representation or guarantee that this software (including any third-party libraries) will perform as intended or will be free of errors, bugs or faulty code. The software may fail which could completely or partially limit functionality or compromise computer systems. If you use or implement it, you do so at your own risk. In no event will Prometeus Network be liable to any party for any damages whatsoever, even if it had been advised of the possibility of damage.

As such this codebase should be treated as experimental and does not contain all currently developed features. Prometeus Network will be delivering regular updates.
