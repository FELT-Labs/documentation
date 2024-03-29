---
description: From creating project to model training.
---

# Complete Getting Started

In this guide, we will use a sample problem to go over all steps necessary for federated learning with FELT. This process consists of:

1. Initial setup
2. Preparing datasets
3. Starting local training
4. Aggregating results from local training
5. Using final model

{% embed url="https://youtu.be/xLcIxxA_9Rs" %}
Video tutorial following similar structure as this guide.
{% endembed %}

## Initial Setup

### Web3 Wallet

For this guide you need an ethereum address. We recommened using MetaMask wallet:

{% embed url="https://metamask.io/download" %}
Follow the instuctions here to download MetaMask
{% endembed %}

For this guide we will be using Polygon Mumbai test network.

_In case you don't have `Polygon Mumbai` network in your MetaMask, you can add it by following_ [_this guide_](https://docs.polygon.technology/docs/develop/metamask/config-polygon-on-metamask/)_._

### Transaction Fees

Right now, the app is deployed on the Polygon Mumbai testnet. First, you will need some MATIC tokens to pay for the transaction fees. You can obtain these using a Polygon faucet. Just visit the following link and paste your wallet address:

{% embed url="https://faucet.polygon.technology" %}
Head to this site to obtain MATIC tokens for paying transaction fees.
{% endembed %}

You will also need OCEAN tokens to pay for datasets and algorithms. You can collect them through OCEAN faucet by submitting your wallet address here:

{% embed url="https://faucet.mumbai.oceanprotocol.com/" %}
OCEAN token faucet for mumbai network.
{% endembed %}

## Preparing datasets

For the demonstration of federated learning, let’s imagine two towns collaborating on analyzing housing data. The data might contain sensitive information. Therefore, they can’t fully disclose the data. Each town publishes its dataset on Ocean, allowing only computation over data without direct access. **We will try to predict a house price based on house parameters** (size in square feet, number of bedrooms, bathrooms, material, etc.). Below you can see a demonstration of our data ([original data file](https://github.com/ywchiu/riii/blob/cba34bb9342cb0d283b531f5dc502fc15688078a/data/house-prices.csv)).

{% embed url="https://gist.github.com/Breta01/4c61088296fdeee2481cf33379d0a31e#file-house-prices-example-csv" %}
Example of house prices dataset. The target column we want to predict (prices) is the last. In data published on Ocean, we also need to remove the header row.
{% endembed %}

We already have the data published on Ocean (using the Mumbai chain) as the following assets, which we will use in this guide:

* [did:op:3632e8584837f2eac04d85466c0cebd8b8cb2673b472a82a310175da9730042a](https://market.oceanprotocol.com/asset/did:op:3632e8584837f2eac04d85466c0cebd8b8cb2673b472a82a310175da9730042a)
* [did:op:cad4a81c9a8e1c1071ccf3e9dea6f8f42d58e100fa3ddf2950c8f0da9e0dda46](https://market.oceanprotocol.com/asset/did:op:cad4a81c9a8e1c1071ccf3e9dea6f8f42d58e100fa3ddf2950c8f0da9e0dda46)

### Data Format <a href="#6b53" id="6b53"></a>

In this guide we will be using FELT algorithms. For that we need to have data in the correct data format. Right now, we support only **CSV format**. With the following rules:

* CSV contains only numerical data
* CSV doesn't contain the header row
* All datasets used during training must have the same number of columns

You can check this file [`house-prices-part1.csv`](https://gist.github.com/Breta01/a8482d3cae0c257e9a7394ca72fdb281) which is used in this article. For more details about publishing your datasets on the Ocean marketplace, please read:

{% embed url="https://docs.oceanprotocol.com/using-ocean-market/marketplace-publish-data-asset" %}

{% hint style="info" %}
If you are using your data, don’t forget to allow the “Local Training — FELT” algorithm or just all published algorithms.
{% endhint %}

## Starting Local Training <a href="#901e" id="901e"></a>

Now that we have our data ready. It’s time to start the training! Head to the [app.feltoken.ai](https://app.feltoken.ai/). Before you begin, you need to sign in to FELT.

Then you will select between training on single dataset or on multiple datasets. For our case we will use the **multiple datasets** option. In the first step you will fill in the name of training (you can pick an arbitrary one) and search for our datasets with following dids:

```
did:op:3632e8584837f2eac04d85466c0cebd8b8cb2673b472a82a310175da9730042a
did:op:cad4a81c9a8e1c1071ccf3e9dea6f8f42d58e100fa3ddf2950c8f0da9e0dda46
```

<figure><img src="../.gitbook/assets/guide-step1.png" alt=""><figcaption><p>Screenshot of how the form should look before you go to next step.</p></figcaption></figure>

Then you proceed to the next step, where you select the algorithm you want to run. Pick `Local Training - FELT (DEV)`

<figure><img src="../.gitbook/assets/guide-step2.png" alt=""><figcaption><p>Select the algorithm.</p></figcaption></figure>

In the final step you customize parameters of the algoritm. FELT algorithm lets you pick from different models and customize their parameters. Right now, you can pick from scikit-learn models or analytics (mean, variance...). For our case we can pick any regression model, for example **Ridge regression**.

One of the most important options is to pick **target column index**. This is the index representing column which we want to predict. Setting value to -1 will use the last column. You can click on submit once you select you hyperparameters.

<figure><img src="../.gitbook/assets/guide-step3.png" alt=""><figcaption><p>Picking parameters for the selected model. Target column set to -1 means that we want to predict the last column.</p></figcaption></figure>

### Approving Transactions <a href="#4d63" id="4d63"></a>

Once you hit **Submit** button, you will see the summary and then 2 options how to start the traing. Each option is further described here:

{% content-ref url="start-training.md" %}
[start-training.md](start-training.md)
{% endcontent-ref %}

For this guide, we will be using browser flow without auto-sign. You will have to approve a few transactions using MetaMask to start the training. Make sure that you connected your Metamask and that you are connected to `Polygon Mumbai` test network. Here is the list of all transactions you will have to confirm:

1. Approve OCEAN token spend to purchase the dataset
2. Purchase the dataset _(now approve and purchase are separate transactions)_
3. Approve OCEAN token spend to purchase FELT algorithm for training
4. Purchase the algorithm
5. Sign request to start the compute job (training)

We are starting the training on two datasets; therefore, you will have to approve those transactions twice.

<figure><img src="../.gitbook/assets/guide-approve-tx.png" alt=""><figcaption><p>Screenshot from starting training and approving transactions through MetaMask.</p></figcaption></figure>

## Starting Aggregation <a href="#78b8" id="78b8"></a>

Once you start the local training, you can go to [launched jobs page](https://app.feltlabs.ai/jobs) (you can use **Launched jobs** button). Here you can monitor the progress.

Once both jobs finish, you can start the aggregation. On right side of each local training you have check box which you can use to select which local trainings should be aggregated (you need to select at least 2). After selecting jobs to aggregate, you can click **Aggregate** button and start the aggregation.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Displaying job status; selecting jobs to aggregate and starting the aggregation.</p></figcaption></figure>

After starting the aggregation, the progress bar will pop up. You will have to approve the following transactions:

1. Sign URLs to access local models
2. Approve OCEAN token to pay for provider fees
3. Order dataset for the compute job
4. Approve OCEAN token spend to purchase FELT algorithm for aggregation
5. Purchase the algorithm
6. Sign request to start the compute job (aggregation)

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

## Use Final Model <a href="#93d9" id="93d9"></a>

You can watch aggregation progress. Once it finishes, you will see the **Download final model** button. You will sign the request and download the final model (in our case `final-model-House Prices.json`). The file is not a standard machine learning file format. You will have to use the FELT library to import it.

First, you have to install the [FELT python library](https://github.com/FELT-Labs/feltlabs.py) using pip (it requires **Python 3.9 or newer**):

```
pip install feltlabs
```

Then you can load the model using `feltlabs.model.load_model(model_path)` function. This function will take the path of the model file as an argument and return the model object.

When using the federated learning option and importing the model using `load_model(...)` function. The function returns the model, which can be used as a standard [scikit-learn model](https://scikit-learn.org/stable/modules/generated/sklearn.linear\_model.LinearRegression.html) object. The model can then be used for prediction using the function `model.predict(data)`. You can check the following code for sample usage:

{% embed url="https://gist.github.com/Breta01/96f9c3783e18260bb6b512b1c3f94a68#file-felt-load-model-py" %}

That’s it. You just trained your first model on a distributed dataset! Now it’s up to your imagination to find projects where you can use this technology.

## Conclusion

These should be the main parts for getting started with the FELT. In the following guides, you might find more detailed instructions for specific tasks.
