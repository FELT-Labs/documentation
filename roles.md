# Roles

{% hint style="info" %}
When referring to the **user** we mean a single blockchain address.
{% endhint %}

In FELT, we define two main roles: data scientist and data provider. The data provider is anyone publishing their data on Ocean protocol. The data scientist is then a person who selects suitable datasets and starts the training. Data provider or data scientist can be any kind of entity (person, company, etc.) with the ability to publish data or start training.

### Data Scientist

{% hint style="info" %}
Data scientist trains ML models on the datasets.
{% endhint %}

A data scientist is the person picking datasets and running machine learning on them. The process of training can be started through FELT application: [app.feltlabs.ai](https://app.feltlabs.ai/). In the application, he can pick dataset ids (DIDs), specify the model type and start the training. In order to be able to run the training, the data scientist must pay the necessary fees for training a purchasing the data from data providers. After that, he or she can monitor training progress and initiate the creation of the final (global) model.

For more details, read:

{% content-ref url="guides/getting-started.md" %}
[getting-started.md](guides/getting-started.md)
{% endcontent-ref %}

### Data Provider

{% hint style="info" %}
The data provider owns private data and provides them on Ocean protocol.
{% endhint %}

Data providers are data owners. They can publish their data on Ocean protocol and make them available for computation. By doing that, they can also specify the price for using their data. They can control which algorithms can be used on top of their data; therefore, data providers must approve the FELT local training algorithm. They also have to ensure that their data are in a format compatible with FELT.

For more details, read:

{% content-ref url="guides/data-provider.md" %}
[data-provider.md](guides/data-provider.md)
{% endcontent-ref %}
