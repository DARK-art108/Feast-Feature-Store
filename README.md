## Feast with local as a Online Store

This Project aims at showing the use of Feature Store in MLOps to store and retrieve features from a local filesystem which is used as Online Store.

Feature Store is pretty much used in every large scale ml project and many big firms like netflix, gojek, uber, etc. use it to store their features.

### Architecture of Feature Store:

![](https://raw.githubusercontent.com/DARK-art108/Feast-Feature-Store/main/utils/feast.png)

To make this project work, we need to use the following steps:

1. Install Feast: `pip install feast`
2. Run: `feast init -n breast_cancer`
3. Run: `data_generation.ipynb` notebook to generate data
4. Make Changes in feature_store.py to change the path of the data and the name of the feature store
5. Run: `definitions.py` to generate schema
6. Run: `create_dataset.py` to create dataset
7. Run: `train.py` to train the model and save the model
8. Run: `materialize.py` to materialize to update the feature store with recent features.
9. Run: `predict.py` to predict the data and save the predictions to prediction.csv.

## Some things to note:

**Online vs Offline Feature Store:**

**Online** – In online mode, features are read with low latency (milliseconds) reads and used for high throughput predictions. This mode requires a feature group to be stored in an online store. 

**Offline** – In offline mode, large streams of data are fed to an offline store, which can be used for training and batch inference. This mode requires a feature group to be stored in an offline store.

***We have used an online store in this project, to get low latency reads and high throughput predictions.***

**Error you will face while using this project:**

**Path Issue**: Sometimes you need to debug the path issue. You can use `pwd` to check the current directory and fix the file not found error.Or you can move the file into the feature store directory.But make to remove the files from feature store directory after training model, to maintain the cleanliness of the feature store.

That's all folks!



