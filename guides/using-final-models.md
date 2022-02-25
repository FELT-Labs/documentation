# Using Final Models

Right now FELToken supports only **scikit-learn** models. Models are exported using **joblib** library. That means that you need correct version of the **joblib** and **scikit-learn** libraries. You can find these in [felt package requirements](https://github.com/FELToken/federated-learning-token/blob/main/requirements-lib.txt).

```
joblib==1.1.0
numpy==1.21.0
scikit-learn==1.0.1
```

If you created a plan, you can watch it in the project dashboard. Once the plan is finished, you should see a download button next to it (this is only available to builder who created the training plan). By clicking the **DOWNLOAD** button you will obtain the model. The model is encrypted. Before the download starts, you will see a MetaMask pop-up asking you to decrypt the data (the model). After approving the decryption, you should receive `model.joblib` file. In your Python code, you can use this file as follows:

```
import numpy as np
import joblib

# Load the model, use the correct path to the model.joblib file
model = joblib.load("model.joblib")

print("Model details:", model.__dict__)

# X should contain the data you want to use for prediction
X = np.array([...])
result = model.predict(X)
```

**Important:** In order to run this code you need correct version of the joblib and scikit-learn libraries. You can find these in [felt package requirements](https://github.com/FELToken/federated-learning-token/blob/main/requirements-lib.txt).

```
joblib==1.1.0
numpy==1.21.0
scikit-learn==1.0.1
```
