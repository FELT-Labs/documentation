# Federated Learning

Federated learning is a powerful technique that enables multiple parties to collaborate on training a single machine learning model while keeping their private data secure. For example, three separate companies might want to create a machine learning model to improve their product recommendations, but they don't want to share their data with each other. With federated learning, each company trains a local model on its own data. These local models are then combined to create a global model that's better than any of the local models individually, while ensuring that no sensitive data is revealed during the process.

{% hint style="info" %}
There are many applications where companies/individuals can make use of federated learning:

* Car manufacturers sharing self-driving data
* Hospitals developing AI to treat patients better
* Individuals sharing data from fitness tracking devices
* Ecommerce providing better products to customers&#x20;
{% endhint %}

FELT makes federated learning simple by providing its own algorithms for training and aggregating models. We rely on Ocean protocol to handle everything around data management. Our platform allows data scientists to easily select any compatible data published on Ocean and use it to train their models. They can choose our algorithms or create their own for their specific use case, and run them seamlessly through FELT. Meanwhile, data providers can set prices on their data and get paid for providing compute to their private data.

_There are multiple approaches to federated learning. At the moment, FELT implements only one of them, but we have plans to extend this in the future._
