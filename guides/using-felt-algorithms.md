# Using FELT Algorithms

We provide algorithms that you can use to train scikit-learn models and perform data analytics on CSV data. The general workflow of using the FELT application is described in the following:

{% content-ref url="getting-started.md" %}
[getting-started.md](getting-started.md)
{% endcontent-ref %}

If you need an algorithm for your specific use case, see the following section:

{% content-ref url="creating-custom-algorithms.md" %}
[creating-custom-algorithms.md](creating-custom-algorithms.md)
{% endcontent-ref %}

## Supported models

We are extending the list of supported models. If you request a certain model, we will try to prioritize adding it to our application.

{% embed url="https://github.com/FELT-Labs/feltlabs.py/issues" %}
Here you can create issue - requesting model type
{% endembed %}

### Scikit-learn models

* Regression:
  * [Linear Regression](https://scikit-learn.org/stable/modules/linear\_model.html#ordinary-least-squares)
  * [Ridge Regression](https://scikit-learn.org/stable/modules/linear\_model.html#ridge-regression-and-classification)
  * [Lasso Regression](https://scikit-learn.org/stable/modules/linear\_model.html#lasso)
  * [Elastic-Net](https://scikit-learn.org/stable/modules/linear\_model.html#elastic-net)
  * [LARS Lasso](https://scikit-learn.org/stable/modules/linear\_model.html#lars-lasso)
* Classification:
  * [SGD Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.linear\_model.SGDClassifier.html#sklearn.linear\_model.SGDClassifier)
  * [Logistic Regression](https://scikit-learn.org/stable/modules/linear\_model.html#logistic-regression)
* Clustering:
  * [Nearest Centroid Classifier](https://scikit-learn.org/stable/modules/neighbors.html#nearest-centroid-classifier)
* Neural Networks:
  * [MLP Classifier](https://scikit-learn.org/stable/modules/neural\_networks\_supervised.html#classification)
  * [MLP Regressor](https://scikit-learn.org/stable/modules/neural\_networks\_supervised.html#regression)

### Data analytics

* Mean
* Sum
* Variance
* Standard deviation

### TensorFlow models

Coming soon

## Using Final Models

FELT is using custom format (based on JSON) for storing and exchanging the models. When you finish the training, you will download your final model file (e.g. `final-model-House Prices.json`).

In order to use it, you have to install the [FELT python library](https://github.com/FELT-Labs/feltlabs.py) using pip (it requires **Python 3.9 or newer**, the Python 3.9 is recommended):

```
pip install feltlabs
```

Then you can load the model using `feltlabs.model.load_model(model_path)` function. This function will take the path of the model file as an argument and return the model object. Right now, we support two types of models: federated learning and federated analytics. The behaviour of each is slightly different.

#### Federated Learning - Scikit-learn Model

When using the federated learning option and importing the model using `load_model(...)` function, the function returns the model, which can be used as a standard [scikit-learn model](https://scikit-learn.org/stable/modules/generated/sklearn.linear\_model.LinearRegression.html) object. The model can then be used for prediction using the function `model.predict(data)`. You can check the following code for sample usage:

{% embed url="https://gist.github.com/Breta01/96f9c3783e18260bb6b512b1c3f94a68#file-felt-load-model-py" %}

#### Federated Analytics Models

Similarly to federated learning models, these models can be loaded using `load_model(...)` a function. This time you don't have to pass any data to the model, and you can obtain calculated value (of sum, mean, variance, or std) using the `model.predict(None)` function. See the example below:

```python
from feltlabs.model import load_model

# Load model
model = load_model("final-model-mean.json")
# Call predict function without any input
mean = model.predict(None)
print(mean)
# This will print the value of mean calculated by the model
```

### Converting FELT format to Python Pickle format

You can convert the FELT model format into a standard pickle file. This file will then contain a pickled object of scikit-learn model. FELT library provides an easy command for that. After installing `feltlabs.py` library, you can run:

```
felt-export --input "final-model-House Prices.json" --output "model.pkl"
```

Then you can use the created file as follows:

```python
import pickle

with open('model.pkl', 'rb') as f:
    model = pickle.load(object, f)
    
# See the above code example for data definition
model.predict(data)
```
