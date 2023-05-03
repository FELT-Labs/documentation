# What is FELT Labs?

FELT Labs is a data sciense company. We are providing a set of tools for doing data sciencse on private and distributed data. Currently we are focusing on federated learning on top of the Ocean Protocol. Ocean creates tools for web3 data economy. We allow you to pick datasets from Ocean (any number of them) and train machine learning models or run data analytics across all of them. We also guarantee to preserve data privacy so that individual data aren't revealed. The core of FELT Labs is our web application, allowing users to run the whole process of training seamlessly.

### Federated Learning & How FELT Works

Federated learning is a process of training a single machine learning model by multiple parties with private data.

For example, you can imagine three separate companies who decide to cooperate on creating a machine learning model which would help them predict better product recommendations to the customers. However, data owned by these companies might be private, or they simply don't want to share data with others to keep some advantage. With federated learning, each company trains the model separately on its data. This local model is then combined with others into one global model. The global model is better than each local model individually. Moreover, the sensitive data aren't revealed to others during this process.

{% hint style="info" %}
There are many applications where companies/individuals can make use of federated learning:

* Car manufactures working on self-driving tehcnology
* Hospitals developing AI to treat patients better
* Individuals sharing data from fitness tracking devices
* Ecommerce providing better products to customers
{% endhint %}

FELT makes this process simple by providing our own algorithms for training the models and then aggregating them. We rely on Ocean protocol to handle everything around data management. All models are encrypted during the exchange, so only approved parties can use them. Data scientists can pick any compatible data published on Ocean protocol and use them for training. They can use algorithms provided by FELT or even create algorithms for their specific use-case and then simple run them through FELT. Finally, data providers can set prices on their data and get paid for providing their data.

_There are multiple approaches to federated learning. At the moment, FELT implements only one of them, but we have plans to extend this in the future._

### Benefits

Key benefits of FELT:

1. **Secure** - all data remains securely on the data provider machine. Architecture is protected by a blockchain network.
2. **Encrypted** - all trained models are encrypted and exchanged only between interested parties.
3. **Easy** - running the whole process is very simple.
4. **Rewards** - data providers get rewards for providing data.

## Getting Started

**Have 2 minutes?**&#x20;

{% embed url="https://youtu.be/gRqWCdeTIDo" %}
FELT Labs promotion video.
{% endembed %}

**Have 5 minutes?**&#x20;

{% embed url="https://www.youtube.com/watch?v=CFfmLdYtz4s&t=5s" %}
Presentation of FELT Labs architecture
{% endembed %}

### Guides: Jump right in

Follow our handy guides to get started on the basics as quickly as possible:

{% content-ref url="guides/getting-started.md" %}
[getting-started.md](guides/getting-started.md)
{% endcontent-ref %}

{% content-ref url="guides/data-provider.md" %}
[data-provider.md](guides/data-provider.md)
{% endcontent-ref %}

### Fundamentals: Dive a little deeper

Learn the fundamentals of FELT to get a deeper understanding of our main features:

{% content-ref url="fundamentals/federated-learning.md" %}
[federated-learning.md](fundamentals/federated-learning.md)
{% endcontent-ref %}

{% content-ref url="fundamentals/felt-architecture.md" %}
[felt-architecture.md](fundamentals/felt-architecture.md)
{% endcontent-ref %}
