# Using Final Models

Right now FELToken supports only **scikit-learn** models. FELT is using custom format (based on JSON) for storing and exchanging the models. When you finish the training, you will download your final model file (e.g. `final-model-House Prices.json`).

In order to use it, you have to install the [FELT python library](https://github.com/FELT-Labs/feltlabs.py) using pip (it requires **Python 3.9 or newer**, the Python 3.9 is recommended):

```
jpip install feltlabs
```

Then you can load the model using `feltlabs.model.load_model(model_path)` function. This function will take the path of the model file as an argument and return the standard [scikit-learn model](https://scikit-learn.org/stable/modules/generated/sklearn.linear\_model.LinearRegression.html) object. You can check the following code for sample usage:

{% embed url="https://gist.github.com/Breta01/96f9c3783e18260bb6b512b1c3f94a68#file-felt-load-model-py" %}

### Converting FELT format to Python Pickle format

You can convert FELT model format into standard pickle file. This file will then contain pickled object of scikit-learn model. FELT library provides easy command for that. After installing `feltlabs.py` library, you can run:

```
felt-export --input "final-model-House Prices.json" --output "model.pkl"
```

Then you can use the created file as follows:

<pre class="language-python"><code class="lang-python"><strong>import pickle
</strong><strong>
</strong><strong>with open('model.pkl', 'rb') as f:
</strong>    model = pickle.load(object, f)
    
# See the above code example for data definition
model.predict(data)</code></pre>
