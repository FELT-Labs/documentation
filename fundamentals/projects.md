# Projects

Projects are the building blocks of FELToken. Each project is represented by single smart contract. A projects represents a single distributed dataset. That means that in one project can participate multiple data providers with compatible data.

This smart contract manages interactions between data providers and builders. It also controls the training process acting as a decentralized logging system. This ensures fairness in the training process. The smart contract also controls exchange of the public keys and encryption keys, so that builders and data providers can securely exchange encrypted models. By encrypting models we make sure that only authorised user can use them.

Each project can train multiple machine learning models. These are usually denoted as **training plans**. Training plans define the model and how it should be trained. They are defined by builders and then executed by data providers.

{% content-ref url="training-plans.md" %}
[training-plans.md](training-plans.md)
{% endcontent-ref %}

There are three main roles: viewers, builders, and data providers. This roles always relates to single project. You can read more about individual roles at:

{% content-ref url="../roles.md" %}
[roles.md](../roles.md)
{% endcontent-ref %}
