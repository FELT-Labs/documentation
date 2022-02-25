# What is FELToken?

{% hint style="info" %}
**FELT** is short for Federated Learning Token
{% endhint %}

FELT is a set of tools for running federated learning on blockchain. In general, during federated learning interested parties must set up the main server for managing the process. We want to replace this server with a smart contract, making the setup simpler and bringing extra security benefits. The core of FELToken are a set of smart contracts, a python package for running the node (being data provider), and a web application for interacting contracts.

### Federated Learning & How FELToken Works

The federated learning denotes process of training single machine learning model by multiple parties with private data.

For example you can imagine three separate companies who decide to cooperate on creating machine learning model which would help theme predict better product recommendations to the customers. However data owned by these companies might be private or they simply don't want to share data with others to keep some advantage. With federated learning each company trains the model separately on their data. Companies then exchange only the final models which are combined into single model better than each model individually.

{% hint style="info" %}
There are many applications where companies/individuals can make use of federated learning:

* Car manufactures creating self driving
* Hospitals developing AI to better treat patients
* Individuals sharing data from fitness tracking devices
* Ecommerce providing better products to customers&#x20;
{% endhint %}

FELToken makes this process simple by providing our own software for training the models and then aggregating them. We use blockchain in order to ensure fairness of the process and mange exchange of the models. All models are encrypted during exchange so only approved parties can use them. Furthermore data providers (companies/individuals) can join and anonymously provide data. This also allows data scientists to work with private data without compromising their privacy. Finally we can reward data providers for their participation in training

_There are multiple approaches to federated learning. At the moment FELToken implements only one of them, but we have plans to extend this in the future._

__

### Smart Contracts

As a user, you will be mainly interested in the project contract. A project represents a dataset or a single type of data. When parties decide for running a federated learning project, they decide on the type of data. Then they deploy a project contract that allows them to train different models on data. Parties are connected to the contract and running data provider code.

> Projects are the building blocks of our application.

The other important contract is the FELT token which is a basic ERC-20 token. This token is used for rewarding data providers and managing contracts.

### Benefits

Using smart contracts over a central server brings certain benefits.

1. **Secure** - all data remains securely on the data provider machine. Architecture is protected by a blockchain network.
2. **Encrypted** - all trained models are encrypted and exchanged only between interested parties.
3. **Anonymous** - parties can anonymously participate in different federated learning projects.
4. **Rewards** - data providers get rewards for participating in projects. Rewards depend on the quality of data.

## Getting Started

**Got 5 minutes?** Here is the submission video from Chainlink Hackathon 2021 during which was the project started:

{% embed url="https://youtu.be/3TFzvjnEDAA" %}

### Guides: Jump right in

Follow our handy guides to get started on the basics as quickly as possible:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### Fundamentals: Dive a little deeper

Learn the fundamentals of FELT to get a deeper understanding of our main features:

{% content-ref url="fundamentals/federated-learning.md" %}
[federated-learning.md](fundamentals/federated-learning.md)
{% endcontent-ref %}

{% content-ref url="fundamentals/projects.md" %}
[projects.md](fundamentals/projects.md)
{% endcontent-ref %}

