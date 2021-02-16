<img src="https://i.imgur.com/iMVIxCH.png" width="500px">

## Scenario and Why Domain Adversarial Training

In this project, we have labels with source data and no label with target data. The problem is that the source data and target data are not identical in nature (or, not from the same distribution), but there may have some correlations. 

How could you maximize the resources that you have in hand to predict the target data with the labelled source dataset and unlabelled target dataset?

If you adopt the conventional method that uses Deap Neural Network that trains the source dataset and predict on the target dataset, the result is highly likely to turn out to be a mess (e.g. Anomaly Detection), because the target data are anomaly in the view of source data. 

For example, if we have the following the neural network:

<img src="https://i.imgur.com/IL0PxCY.png" width="500px">

It can accuratelly predict test prictures with the same distribution from source data but cannot predict target data at all. The Feature Extractor does not "learn about" some features from traget data and thus may not give a good prediction.

However, this drawabck can be complemented by the domain adversarial training. 

## Domain Adversarial Training of Nerural Networks (DaNN)

**DaNN complements this drawback by training a feature extractor that maps both the source data and target data to the same distribution after the extraction process**, and then feeds these features (in the same distribution) to classifier. 


<img src="https://i.imgur.com/vrOE5a6.png" width="500px">


It's realized by connecting a Domain Classifier to feature extractor. Feature extractor learns not only how to minimize loss of classifier but also maximize loss of domail classifier, **which means the network cannot tell the difference between source and target**. 

Paper: https://arxiv.org/pdf/1505.07818.pdf
Dataset: real_or_painting
