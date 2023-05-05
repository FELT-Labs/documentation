# Data Provider

A data provider is someone who publishes data on Ocean Protocol. They can choose to use a trusted Ocean provider or run their own. When publishing data, they set various parameters, such as the name, description, and price of the dataset.

If you are publishing private data, you only provide compute access and not download access. Therefore, you need to specify which algorithms can run on your data. To allow FELT algorithm, you need to ensure that your data are in the correct format for the algorithm to load the data and train models.

In general, data scientists need to be aware of format of the data and its schema so they can create a meaningful algorithm. On the other hand, data providers need to be awere of the algorithm that data scientist wants to run. If data provider wants to allow this algorithm to be run on their data, they need to specify it when publishing to Ocean (or later by editing the metadata).

### Data provider vs Ocean provider

To prevent any confusion between these two terms, the data provider is the entity owning the data. Ocean provider is code that is running on some machine. Ocean provider code interacts with Ocean smart contracts, handles the dataset purchases, and runs the computation with data.

Therefore, when data providers decide to publish data on Ocean, they must pick some Ocean provider which will manage the data access for them. Data providers can either pick some public Ocean provider or run their own instance of Ocean provider in order to reach the maximum security of the data.

_Keep in mind that once you publish your data, the Ocean provider code has full access to your data. Hence you must trust the entity running the Ocean provider (you can also be the one running the Ocean provider)._

### Data Format for using FELT algorithm

If you want to use FELT algorithm with your own data, you first need to have data in the correct data format. Right now, we support only **CSV format**. With the following rules:

* CSV contains only numerical data
* CSV doesn't contain the header row
* All datasets used during training must have the same number of columns

You can check this file [`house-prices-part1.csv`](https://gist.github.com/Breta01/a8482d3cae0c257e9a7394ca72fdb281) as an example.

### Publishing data

Publishing data can be done through Ocean marketplace. The web application will walk you through the whole process. For more details, please read:

{% embed url="https://docs.oceanprotocol.com/using-ocean-market/marketplace-publish-data-asset" %}

Alternatively, you can use their libraries - [ocean.py](https://github.com/oceanprotocol/ocean.py) or [ocean.js](https://github.com/oceanprotocol/ocean.js)

Don't forget to allow algorithms to run on your data.
