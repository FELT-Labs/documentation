# Roles

In FELT, we define two main roles: data scientist and data provider. The data provider is anyone publishing their data on Ocean Protocol. The data scientist is then a person who selects suitable datasets and starts the training. Data provider or data scientist can be any kind of entity (person, company, etc.) with the ability to publish data or start training.

### Data Scientist

{% hint style="info" %}
Data scientist trains ML models on the datasets.
{% endhint %}

A data scientist is the person picking datasets and analyzing them or running machine learning on them. The process of training can be started through FELT application: [app.feltlabs.ai](https://app.feltlabs.ai/). In the application, the data scientist can start the training simply with 3 steps - pick datasets, pick algorithm to run on those datasets and specify optional parameters. In order to be able to run the training, the data scientist must pay the necessary fees for training algorithms and purchasing compute access to the data from data providers. After that, they can monitor training progress and download the final global model.

For more details, read:

{% content-ref url="guides/getting-started.md" %}
[getting-started.md](guides/getting-started.md)
{% endcontent-ref %}

### Data Provider

{% hint style="info" %}
The data provider owns private data and provides compute access to them via the Ocean Protocol.
{% endhint %}

Data providers are data owners. They can publish their data on Ocean protocol and make them available for computation. By doing that, they can also specify the price for using their data. They can control which algorithms can be used on top of their data (e.g. FELT local training algorithm).

For more details, read:

{% content-ref url="guides/data-provider.md" %}
[data-provider.md](guides/data-provider.md)
{% endcontent-ref %}
