# Data Provider

A data provider is anybody who publishes data on Ocean Protocol. When publishing data, you can either pick a trusted Ocean provider or run your own Ocean provider. Ocean provider then runs all the computation with your data. While publishing data you can set different dataset parameters like name, description, price, etc.

When publishing private data, you don't provide download access but only compute access. For that you need to specify which algorithms can run on top of your data. If you want to allow FELT algorithm, the most important part is to ensure that published data are in the correct format. This is necessary so that FELT algorithms can load data and train the models.

In general data scientists need to be aware of format of the data and its schema so they can create a meaningful algorithm. Data providers need to be awere of the algorithm that data scientist wants to run. If data providers allow this algorithm to be run on their data, they need to specify it in the metadata.

### Data provider vs Ocean provider

To prevent any confusion between these two terms, the data provider is the entity owning the data. Ocean provider is code that is running on some machine. Ocean provider code interacts with Ocean smart contracts, handles the dataset purchases, and runs the computation with data.

Therefore, when data providers decide to publish data on Ocean, they must pick some Ocean provider which will manage the data access for them. Data providers can either pick some public Ocean provider or run their own instance of Ocean provider in order to reach the maximum security of the data.

_Keep in mind that once you publish your data, the Ocean provider code has full access to your data. Hence you must trust the entity running the Ocean provider (you can also be the one running the Ocean provider)._

### Data Format for using FELT algorithm

If you want to use FELT algorithm with your own data, you will first need to have data in the correct data format. Right now, we support only **CSV format**. With the following rules:

* CSV contains only numerical data
* Remove header row from data
* All datasets used during training must have the same number of columns

You can check this file [`house-prices-part1.csv`](https://gist.github.com/Breta01/a8482d3cae0c257e9a7394ca72fdb281) for an example of a data file (**the last column is the target column** other columns are used as features).

### Publishing data

Publishing data can be done through Ocean marketplace. The web application will walk you through the whole process. For more details, please read:

{% embed url="https://docs.oceanprotocol.com/using-ocean-market/marketplace-publish-data-asset" %}

### Approve FELT Algorithms

If you are using your data, don’t forget to allow the “Local Training — FELT” algorithm.
