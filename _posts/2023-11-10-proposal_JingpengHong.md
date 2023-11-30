---
layout: distill
title: Recurrent Recommender System with Incentivized Search
description: This project considers the use of Recurrent Neural Networks (RNNs) in session-based recommender systems. We input sequences of customers' behavior, such as browsing history, to predict which product they're most likely to buy next. Our model improves upon this by taking into account how previous recommendations influence subsequent search behavior, which then serves as our training data. Our approach introduces a multi-task RNN that not only aims to recommend products with the highest likelihood of purchase but also those that are likely to encourage further customer searches. This additional search activity can enrich our training data, ultimately boosting the model's long-term performance.

date: 2022-12-01
htmlwidgets: true

authors:
  - name: Jingpeng Hong
    url: "https://jingpenghong.github.io/"
    affiliations:
      name: Harvard Business School
      
bibliography: 2022-12-01-distill-example.bib  

toc:
  - name: Proposal
  - name: Plan

---

## Motivation 

Numerous deep learning based recommender systems have been proposed recently <d-cite key="10.1145/3285029"></d-cite>. Especially, the sequential structure of session or click-logs are highly suitable for the inductive biases provided by recurrent/convolutional neural networks <d-cite key="hidasi2016sessionbased"></d-cite>. In such setting, the input of the network is a sequence of consumers' search behavior, while the output is the predicted preference of the items, i.e. the likelihood of being the next in the session for each item. The ultimate goal is to pinpoint the optimal product for the consumer, thereby increasing sales. An example of where this could be applied is the "featured product" on platforms like Amazon.

However, a challenge with this model is the sparsity of data. It's well-known that the products in retail has the "long-tail" feature. Only a small fraction, say 5%, of a site's products are ever browsed or bought by customers, leaving no data on the remaining products. Additionally, customer sessions tend to be brief, limiting the amount of information we can get from any one individual. This issue is particularly acute for "data-hungry" models, which may not have sufficient training data with enough variation to accurately match products with customers.

My proposed solution to this issue is to recommend products that also encourage further exploration. Economic studies have shown that certain types of information structure can motivate customers to consider more options, harnessing the "wisdom of crowds" <d-cite key="kremer2014implementing"></d-cite><d-cite key="che2018recommender"></d-cite>. Imagine two products: recommending the first leads to a 5% purchase likelihood, while the second has a 4% chance. But the second item prompts the customer to look at 5 additional products. This extra data allows our model to learn more, potentially enhancing recommendations for this and other customers in the future. Therefore, we might choose to recommend the second product to generate more user-driven training data.

## Plan 

For the first step, we aim to improve Recurrent Neural Networks (RNNs) by incorporating multi-task learning, focusing on two objectives: i) predicting the likelihood of an item being the next viewed in a session ii) predicting the number of items a customer will browse next. Undertaking this task requires more knowledge in RNNs, particularly LSTMs, and multi-task deep learning.

For the second step, our goal is to gather established models like matrix factorization (MF) and deep learning-based collaborative filtering (CF) to use as benchmarks. I intend to carry out an extensive review of the literature to select popular methods for comparison.

For the final step, we plan to create simulations of consumer search behavior to observe how they interact under various conditions by the recommender system. This involves defining specific search behaviors and determining whether our approach indeed prompts more extensive searching by the user. Subsequently, we can assess the value of the additional data generated by the consumer's search activity resulting from our recommendations.







