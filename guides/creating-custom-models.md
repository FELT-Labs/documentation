# Creating Custom Models

Defining a custom model is relatively simple. First, you have to install `felt` pip package (this guide was created for version `0.1.0`):

```
pip install git+https://github.com/FELToken/federated-learning-token
```

Then you will need to define API token for the web3.storage as an environment variable:

```
export WEB3_STORAGE_TOKEN='ab...'
```

Then you just need to pick a model from scikit-learn. For example, here we will use linear regression with L2 regularization setting the custom value of alpha. After defining the model you just need to pass it to `upload_model(model)` function.&#x20;

{% embed url="https://gist.github.com/Breta01/aed22dfd6c46e4fbd0690796549f4d7d#file-defining-custome-model-py" %}
Short script for defining a model and printing the CID.
{% endembed %}

Then just run the code and it will return the model CID which you can then use in web application during training plan definition.
