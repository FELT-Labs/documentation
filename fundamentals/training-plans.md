# Training Plans

Each project can execute training plans. Training plan represents training of single machine learning model. Each project can execute multiple training plans, so you don't have to define new project for each model.

The core of the training plan is definition of machine learning model. Models are stored on IPFS and training plan contains only reference to them using CID.

Training plan also defines number of training rounds. Each round consists of each data provider training the model locally and then aggregating all model together. Performing multiple rounds might be necessary in order to achieve the best results.

Training plan can also define reward for each node for training. This way data providers can be rewarded for providing their data. These rewards are paid in FELToken.
