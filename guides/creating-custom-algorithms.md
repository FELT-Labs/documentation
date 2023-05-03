# Creating Custom Algorithms

FELT Labs currently offers one algorithm that can be used to train certain types of machine learning models or perform data analytics on CSV data. However, if you have a specific use case that requires a different algorithm, we offer two options.

First option, you can tell us what you need and we can create a custom algorithm for you. Once the algorithm is developed, you will be able to easily run it on your data. To request a custom algorithm, you can reach out to us on our Discord channel and provide us with the details of your use case.

Second option, you can build your own algorithm. We provide instructions on how to do this in the following sections of our documentation. We encourage you to let us know if you decide to build your own algorithm, so that we can assist you and ensure that the final product meets your needs.

Overall, our goal is to provide our users with flexible options for using our platform and to ensure that they are able to achieve their specific data analysis and machine learning objectives, whether that involves using our pre-existing algorithm or developing a custom solution.

## How to Build a Custom Algorithm
To create algorithms that are tailored to your specific use case, you will need to develop two separate algorithms: one for local training and another for aggregation. The local training algorithm runs on the data iteself, computing intermediate results. Those results are then aggregated with the aggregation algorithm.

We provide a simple example of what such a pair of algorithms looks like in our GitHub repository, which you can find here:

{% embed url="https://github.com/FELT-Labs/base-algorithm" %}
Simple example to demonstrate how algorithms should look like
{% endembed %}

You can also check out the implementation of our existing algorithms here:

{% embed url="https://github.com/FELT-Labs/feltlabs.py/tree/main/feltlabs/algorithm" %}
FELT Labs algorithms
{% endembed %}

Once you have developed your algorithms, you will need to publish them as two separate algorithm assets on the Ocean Protocol. Instructions for doing so can be found at the following link: 

{% embed url="https://docs.oceanprotocol.com/using-ocean-market/marketplace-publish-data-asset" %}
Tutorial to publish assets using the Ocean Market
{% endembed %}

After you have developed and published your algorithms, please let us know so that we can review them. Once they are approved, we will list them on our platform, making them available to other users who may benefit from them. Our goal is to help you create algorithms that meet your specific needs and to foster collaboration and innovation in the data science community. If you have any questions don't hesitate to reach out to us.
