# Federated Learning

Federated learning is a process of training a single machine learning model by multiple parties with private data.

For example, you can imagine three separate companies who decide to cooperate on creating a machine learning model which would help them predict better product recommendations to the customers. However, data owned by these companies might be private, or they simply don't want to share data with others to keep some advantage. With federated learning, each company trains the model separately on its data. This local model is then combined with others into one global model. The global model is better than each local model individually. Moreover, the sensitive data aren't revealed to others during this process.

{% hint style="info" %}
There are many applications where companies/individuals can make use of federated learning:

* Car manufacturers sharing self-driving data
* Hospitals developing AI to treat patients better
* Individuals sharing data from fitness tracking devices
* Ecommerce providing better products to customers&#x20;
{% endhint %}

FELT makes this process simple by providing our own algorithms for training the models and then aggregating them. We rely on Ocean protocol to handle everything around data management. All models are encrypted during the exchange, so only approved parties can use them. Data scientists can pick any compatible data published on Ocean protocol and use them for training. Finally, data providers can set prices on their data and get paid for providing their data.

_There are multiple approaches to federated learning. At the moment, FELT implements only one of them, but we have plans to extend this in the future._
