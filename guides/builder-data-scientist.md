# Builder (Data Scientist)

The builder role is assigned to data scientist or people who will define machine learning models which will be trained on the project. The builder can access only the final model produced from training.

## Adding Builder

In order to become a builder, you first have to request an access to the project. This is done through the project dashboard.

{% hint style="info" %}
User refers to a wallet address. In case you don't see the request buttons, make sure that you connected your MetaMask wallet.
{% endhint %}

At first, you go to the project dashboard. Here on left side panel in the builder section is **REQUEST ACCESS** button. After clicking it the request process starts. You will be asked to provide a public key (used for exchanging encrypted models) and send request transaction.

The request then must be accepted by another builder (e.g. project creator). Accepting request is done through project dashboard as well. Any builder viewing the dashboard will see a list of requests with accept or reject buttons next to them. Accepting and rejecting request is fairly straight forward you just click the button and approve the transaction in MetaMask.

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

After filling these information you can click **DEPLOY** button. You will then have to approve the transaction in MetaMask and that's it. You created the training plan which will now be executed by the data providers. You can watch the progress of the training plan in the project dashboard. Once the training is finished, you can download the model using the **DOWNLOAD** button in the dashboard (only builder who created the plan can download the model). After that head the the page about using the final model:

{% content-ref url="using-final-models.md" %}
[using-final-models.md](using-final-models.md)
{% endcontent-ref %}

_Currently there can be only one training plan executed at the same time._
