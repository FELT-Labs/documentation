# Data Provider

A data provider is key role for each project. You can't train machine learning models without at least one active data provider. A data provider can be anyone who owns private data and what to share them for training. The data provider then runs client code which watches the project smart contract and trains machine learning models according to the plans. The data never leaves a data provider's machine. Only the models are exchanged between each other. Furthermore these models are encrypted so only authorised parties can view them.&#x20;

## Adding Data Providers

In order to become a data provider, you first have to request an access to the project. This is done through the project dashboard.

{% hint style="info" %}
User refers to a wallet address. In case you don't see the request buttons, make sure that you connected your MetaMask wallet.
{% endhint %}

At first, you go to the project dashboard. Here on left side panel in the data provider section is **REQUEST ACCESS** button. After clicking it the request process starts. You will be asked to provide a public key (used for exchanging encrypted models) and send request transaction.

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

You have to change the `example_data.csv` to path to your data in CSV format. In case you want to just test the code you can replace `example_data.csv` with `test`.  This will load demo dataset. Right now the code expects simple CSV file using `,` as delimiter without any headers. The last column of the file will be used as **Y** (target values).

For example, if you have data table with house prices as follows:

| Size (square feets) | Number of rooms | Price (in $) |
| ------------------- | --------------- | ------------ |
| 112                 | 3               | 4000         |
| 150                 | 5               | 8000         |
| 50                  | 1               | 3500         |

Then if you want to predict the house prices, your `data.csv` file should look like this:

```
112,3,4000
150,5,8000
50,1,3500
```

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

