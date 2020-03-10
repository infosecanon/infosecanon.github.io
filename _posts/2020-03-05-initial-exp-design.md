---
layout: post
title: "initial experiment design"
date: 2020-03-05
---

As shown below, I would take the KDD99 dataset and the NSL-KDD dataset, split the data into test and training sets, and train a set of machine learning algorithms. Using the test set I can calculate precision, recall, and the F1 score. These results I can compare to a second set of algorithms trained from pcap datasets.

CTU-13, CICIDS2017, and NIDS-AML would have to undergo preprocessing as they are in their base .pcap forms. According to Sharafaldin et al, they were able to pull 79 features from their pcaps. This can then train the same set of algorithms before also determining precision, recall, and the F1 score. It may be challenging to reverse engineer how they processed their pcaps to get the same features across datasets without their code.

Not shown here: exploratory analysis of the human-generated data. Needs to be evaluated for temporal artifacts and correlated with any strategy declared in the interview.

## Hypothesis
The hypothesis is that our data is harder to train/test on because:
1. It has a diverse protocol variety
2. There are human elements to train/test on that don't follow a script
3. It doesn't only have a subset of attacks (ex: only SSH attacks or only botnet attacks)
4. Updates and network configuration issues are events that are captured in the dataset. These can be anomalies. Most other datasets are either too clean or too simple (virtually none are joined to a domain).

## Steps to complete the experiment
1. Resolve the technical debt
  - Get the human samples analyzed and characterized
  - Get the dataset hosted (as of 3/9/2020 AWS, UNLDR, and Impact Cyber Trust have all turned us down)
2. Determine how preprocessing occurs in CICIDS dataset
  - This same preprocessing will be used on all pcap samples
  - This is how we will compare to prior work
3. Write code for all algorithms to be used (KNN, Adaboost, RF, MLP, QDA, ID3, NB)
4. Find prior work (and hopefully prior code) on KDD99
  - Get a notebook together that test/train/splits on this data
  - Save the results (precision, recall, F1 score)
  - Pickle the trained algorithms
5. Find prior work (and hopefully prior code) on NSL-KDD
  - Get a notebook together that test/train/splits on this data
  - Save the results (precision, recall, F1 score)
  - Pickle the trained algorithms  
6. Use the CICIDS preprocessing on the CTU-13 dataset (or whichever other ones we look at)
7. Use the CICIDS preprocessing on the NIDS-AML (or whichever other ones we look at)
8. test/train/split the preprocessed data on the algorithms to be used
- Save the results (precision, recall, F1 score)
- Pickle the trained algorithms
9. Compare data

## Hard numbers/metrics we can show
Common metrics that seem to appear in dataset papers include:
- number of normal samples : number of attack samples (most datasets in this area are extremely unbalanced as attacks are hard to capture)
- protocol diversity
- number of features (which should be the same number of features from CICIDS - 79)
- P/R/F1 across the algorithms and across datasets


<img src="/assets/030520.png" width="700">
