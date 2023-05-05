# FELT Architecture

FELT consists of two main components: FELT application and algorithms. You can find the application at [app.feltlabs.ai](https://app.feltlabs.ai/). This page exaplains how our algorithms work and how we ensure secure encrypted exchange of results. However FELT also provides an option to run your own algorithm so this guide can help you understand how to create your own.

<figure><img src="../.gitbook/assets/image (4) (2).png" alt=""><figcaption><p>The FELT application is interacting with Ocean protocol. It starts compute jobs and retrieve results.</p></figcaption></figure>

### Video presentation

{% embed url="https://www.youtube.com/watch?v=CFfmLdYtz4s" %}
Video from one of our presentations. Presenting FELT architecture.
{% endembed %}

## Algorithms

Algorithms are assets published on Ocean protocol. In general, algorithms are Docker containers that receive dataset(s) from Ocean protocol, execute some code and return results. This is possible using Ocean [compute-to-data](https://oceanprotocol.com/technology/compute-to-data) technology. FELT uses two main algorithms:

* **Local training algorithm** - for training machine learning models on data
* **Aggregation algorithm** - for combining outputs of local training into a single output

Both algorithms use the same Docker container, which you can find here: [FELT Labs - Docker Hub](https://hub.docker.com/r/feltlabs/feltlabs-py). The only difference between them is the entry command which starts the training or aggregation. The Docker container is a basic Python container with `feltlabs` library. For more details about this container, you can check the feltlabs-py repository:

{% embed url="https://github.com/FELT-Labs/feltlabs.py" %}

### Local Training Algorithm

The local training algorithm is for training machine learning models on Ocean datasets. We have a **single** algorithm for training any type of model. After a user picks datasets and a model type in the application, the application starts the local training algorithm on each dataset separately (if data are at different Ocean providers).

{% hint style="info" %}
In order to run this dataset, the dataset author must first approve to run this algorithm.
{% endhint %}

Consequently, each local training algorithm receives a data and model type definition (JSON object). Based on the model definition, the algorithm initializes the model and trains it on the data.

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption><p>For each dataset we start compute job which outputs the local model.</p></figcaption></figure>

Once the training finishes, the algorithm outputs an encrypted model. The model is encrypted in the following way:

1. Algorithm adds random noise to the model. The random noise is known by user who started the training.
2. Algorithm encrypts the model using the aggregation public key. Only the aggregation algorithm knows the private key to encrypt the model.

These two steps ensure greater privacy of the data. Encryption using an aggregation key ensures that the user can't access the local model directly, but it must first run the aggregation of multiple models. Aggregation provides greater privacy for the local data, keeping only global information.

On the other hand, the aggregation algorithm receives models with random values. Therefore aggregation algorithm can't steal the local models because the true values of the models are hidden.

### Aggregation Algorithm

Once the local training finishes, a user can pick models from local training and start the aggregation. The aggregation algorithm first decrypts the models and performs the aggregation. At the moment, we do the aggregation by averaging over model weights (more types of aggregation will be possible in the future).

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p>The algorithm takes outputs of local training and creates one single model out of them.</p></figcaption></figure>

The aggregation algorithm owns a private key, which is used for decrypting outputs of local training. However, the aggregation doesn't know the random noise which was added to models, so the true values of model parameters are kept secret. The aggregation then outputs one final model (we call this **global model**).

The user then can download the final model through the FELT web application. When downloading the model, the information about random noise is added to the model file. The random noise is then automatically removed when loading the model. Therefore the downloaded model file can be used independently on the user.
