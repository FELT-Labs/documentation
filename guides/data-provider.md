# Data Provider

A data provider is anybody who publishes data on Ocean protocol. The most important part is to ensure that published data are in the correct format. This is necessary so that FELT algorithms can load data and train the models. When publishing data, you can either pick a trusted Ocean provider or run your own Ocean provider. Ocean provider then runs all the computation with your data.  While publishing data you can set different dataset parameters like name, description, price, etc.

### Data provider vs Ocean provider

To prevent any confusion between these two terms, the data provider is the entity owning the data. Ocean provider is code that is running on some machine. Ocean provider code interacts with Ocean smart contracts, handles the dataset purchases, and runs the computation with data.

Therefore, when data providers decide to publish data on Ocean, they must pick some Ocean provider which will manage the data access for them. Data providers can either pick some public Ocean provider or run their own instance of Ocean provider in order to reach the maximum security of the data.

_Keep in mind that once you publish your data, the Ocean provider code has full access to your data. Hence you must trust the entity running the Ocean provider (you can also be the one running the Ocean provider)._

### Data Format

### Publishing data

Publishing data can be done through Ocean marketplace. The web application will walk you through the whole process. For more details please read:

{% embed url="https://docs.oceanprotocol.com/using-ocean-market/marketplace-publish-data-asset" %}

### Approve FELT Algorithms

