# Using Final Models

Right now FELToken supports only **scikit-learn** models. FELT is using custom format (based on JSON) for storing and exchanging the models. When you finish the training, you will download your final model file (e.g. `final-model-House Prices.json`).

In order to use it, you have to install the [FELT python library](https://github.com/FELT-Labs/feltlabs.py) using pip (it requires **Python 3.9 or newer**, the Python 3.9 is recommended):

```
pip install feltlabs
```

Then you can load the model using `feltlabs.model.load_model(model_path)` function. This function will take the path of the model file as an argument and return the model object. Right now, we support two types of models: federated learning and federated analytics. The behaviour of each is slightly different.

#### Federated Learning - Scikit-learn Model

When using the federated learning option and importing the model using `load_model(...)` function. The function returns the model, which can be used as a standard [scikit-learn model](https://scikit-learn.org/stable/modules/generated/sklearn.linear\_model.LinearRegression.html) object. The model can then be used for prediction using the function `model.predict(data)`. You can check the following code for sample usage:

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

You can convert FELT model format into a standard pickle file. This file will then contain a pickled object of scikit-learn model. FELT library provides an easy command for that. After installing `feltlabs.py` library, you can run:

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
