# Federated Learning

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
