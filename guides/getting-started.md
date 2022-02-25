---
description: From creating project to model training.
---

# Getting Started

In this guide we will go over all steps from creating a project to training a machine learning model. The goal of this guide is to go over all necessary parts of FELToken. This process consists of:

1. Creating a project
2. Adding and connecting data providers
3. Training machine learning models
4. Using final models

### Transaction Fees

Right now the project is deployed on Polygon Mumbai testnet. First you will need some MATIC tokens to pay for the transaction fees. You can obtain these using Polygon faucet. Just visit following link and paste your wallet address:

{% embed url="https://faucet.polygon.technology" %}
Head to this site to obtain MATIC tokens for paying transaction fees.
{% endembed %}

### Connecting MetaMask

Right now the application only works with MetaMask wallet. Without MetaMask you can only view already existing projects. For instructions how to install MetaMask please visit:

{% embed url="https://metamask.io/download" %}
Follow the instuctions here to obtain MetaMask
{% endembed %}

Once you have the MetaMask installed, you can head to the FELToken application:

{% embed url="https://feltoken.ai/#/app" %}

Here in top-right corner you should see **CONNECT** button with MetaMask icon. On left is dropdown button with different networks. Make sure that `Polygon Mumbai` is selected and click connect. After that you just need to approve the connection in the MetaMask pop-up window. In case any issues occur, make sure that you have `Polygon Mumbai` network selected in your MetaMask as well.

## Creating Project

Once you have your wallet connected, you are ready to create your first project. Start by clicking the **CREATE PROJECT** button in top-right corner leading to [the create project page](https://feltoken.ai/#/app/create-project). On this page you need to fill up the form providing basic information about the project:

* **Name** - name of the project (63 characters max)
* **Type** - right now there is only one project type
* **Description** - should describe the project and the expected data type and format

After filling these information, click on **DEPLOY** and follow the process. Make sure you don't close the browser tab throughout the whole process. The deployment consists of three steps.

First you will be asked to provide your public key. This is required to secure exchange of models between data providers and builders. Only you can decrypt things encrypted by your public key.

Second step is deploying the project contract. You will be asked to confirm the transaction which includes paying a transaction fee. The deployment may take a while (<1 min) depending on how busy is the network at the moment.

Final step is registering the deployed project contract into the project manager. This allows displaying you project in the list of projects. Again you have to confirm the transaction and wait for it to be processed.

Once finished you should see an address of your project. You can click on this address and go to the project dashboard. As a project creator, you will be assigned both roles of builder and data provider (inactive data provider).

## Adding Data Providers

In order to add data providers to the project, they first have to request an access to the project. This is done through the project dashboard.

{% hint style="info" %}
User refers to a wallet address. In case you don't see the request buttons, make sure that you connected your MetaMask wallet.
{% endhint %}

At first, a user without data provider role goes to the project dashboard. Here on left side panel in the data provider section is **REQUEST ACCESS** button. After clicking it the request process starts. User will be asked to provide a public key (used for exchanging encrypted models) and send request transaction.

The request then must be accepted by another data provider (e.g. project creator). Accepting request is done through project dashboard as well. Any data provider viewing the dashboard will see a list of request with accept or reject buttons next to them. Rejecting request is fairly straight forward you just click the button and approve the transaction in MetaMask. Accepting request requires one more step. You need to obtain data provider common secret and share it with the new data provider. After clicking the button you need to click **Decrypt** in MetaMask pop-up window and everything else will be handled for you.

### Running Data Provider Code

Finally when you are added as data provider to the project, you need to run a local client which will watch the smart contract and train the models on local data. For this you will first be required to install **Python 3.9+**. Then you can install the client code using `pip` as:

```
pip install git+https://github.com/FELToken/federated-learning-token
```

In the project dashboard you will be provided with command which you have to run in order to start the client code. It should look something like this (the contract address and chain ID may differ):

```
felt-node-worker --chain 80001 --contract 0x2249f88C04B09e15B08E722f205d679C6AFC0f4E --account main --data example_data.csv
```

You have to change the `example_data.csv` to path to your data in CSV format. Right now the code expects simple CSV file using `,` as delimiter without any headers. The last column of the file will be used as **Y** (target values).

In case you want to just test the code you can replace `example_data.csv` with `test`.  This will load demo dataset.

Once the code starts, you will be asked to provide your **private key** (it must be the key associated with data provider account). This is required so that the code can do transaction with the project smart contract. You can follow the instruction for obtaining private key from MetaMask here:

{% embed url="https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key" %}
Follow the instructions for obtaining private key and paste it to the terminal.
{% endembed %}

Next you will be asked to provide [web3.storage](https://web3.storage) API token. This token can be obtained for free you just need to register. This token is then used to store encrypted models on IPFS using Filecoin. For more instructions follow:

{% embed url="https://docs.web3.storage/how-tos/generate-api-token" %}
Create an account and follow instruction to obtain the API token.
{% endembed %}

#### Environment Variables (optional)

In case you plan to run the client code more often, you can store the private key and API token as environment variable. The client code will then automatically used them. You can set these variables as:

```
export PRIVATE_KEY='0xc...'
export WEB3_STORAGE_TOKEN='ab...'
```

## Training Machine Learning Models

If you want to create a training plan for training a model, you must have a builder role. The builder role can be obtained in similar way as a data provider role by requesting access in the project dashboard. The builder role is automatically given to the creator of the project. Once you have the appropriate role, you can click **CREATE MODEL** button which will bring you to the training plan definition page.

{% hint style="info" %}
There must be at least one active data provider before you can create the training plan.
{% endhint %}

When defining a training plan there is multiple fields you need to define:

* **Model** - models are stored on IPFS and only their reference (CID) is stored in the training plan. You have to options how to pick the training model. Currently we support only **scikit-learn** library
  * **Predefined model** - option number one is to pick one of predefined models (recommended)
  * **Custom model** - you can defined your own model, export it using joblib and upload it to IPFS. Then you just need to provide CID of your model (more on this in separate guide...)
* **Number of round** - one round consists of each data provider training the model and averaging all the models. This process can be repeated multiple times to achieve the best results.
* **Node reward** - node reward is given to each node after completing one round (at the moment just leave it `0` as you need FELTokens to send these rewards)

After filling these information you can click **DEPLOY** button. You will then have to approve the transaction in MetaMask and that's it. You created the training plan which will now be executed by the data providers. You can watch the progress of the training plan in the project dashboard.

_Currently there can be only one training plan executed at the same time._

## Using Final Model

If you created a plan, you can watch it in the project dashboard. Once the plan is finished, you should see a download button next to it (this is only available to builder who created the training plan). By clicking the **DOWNLOAD** button you will obtain the model. The model is encrypted. Before the download starts, you will see a MetaMask pop-up asking you to decrypt the data (the model). After approving the decryption, you should receive `model.joblib` file. In your Python code, you can use this file as follows:

```
import numpy as np
import joblib

# Load the model, use the correct path to the model.joblib file
model = joblib.load("model.joblib")

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

## Conclusion

These should be the main parts for getting started with the FELToken. In following guides you might find more detailed instructions for specific tasks.
