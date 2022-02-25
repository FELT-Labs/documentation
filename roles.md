# Roles

{% hint style="info" %}
When referring to **user** we mean single blockchain address.
{% endhint %}

In our application we define three main roles: viewer, builder, and data provider. These roles are always associated with given project. You can have builder role in one project and only viewer role in different project. The roles are associated with your blockchain address. You can be both builder and data provider for single project.

### Viewer

{% hint style="info" %}
Viewer can view basic info and request access to a project.
{% endhint %}

The default role for every user is viewer role. Viewer can see the state of a project contract (anybody on blockchain can view this information). This allows user to learn basic information about the project, for example, project name, description, number of participants, etc. All models exchanged as part of the project are encrypted, therefore, viewer can't use them.

Viewer can also request access to become builder or data provider for given project. Access can be requested in web application through project dashboard.

### Builder

{% hint style="info" %}
Builder can train ML models on the project.
{% endhint %}

Builder can create **training plans** for given project. Training plans are definitions of machine learning models plus number of rounds which will be trained by data providers. Once training plan is created, data providers download the plan and start training process. Only builder who created the training plan can download final model.

Other than that builder can also approve/decline requests from viewers to become builders. Builder can also request to become a data provider. All of this can be done through the project dashboard.

### Data Provider

{% hint style="info" %}
Data provider owns private data and use them to train ML models.
{% endhint %}

Data providers are data owners who decide to participate in project. Once you become data provider (sometimes referred as **node**), you have to run the data provider code. This code will watch project contract and executes training plans when they arrive. Data itself never leaves your machine. Only the trained models are exchanged with other data providers and builder.

Data provider can go inactive by deactivating himself through the project dashboard. Data providers can approved incoming data providers. They can also become a builders. &#x20;

### Project Creator

Once the project is created, the user who created it becomes a data provider and builder at the same time. This allows project creator to approve new builders and data providers.
