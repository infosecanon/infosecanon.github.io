---
layout: post
title: "initial experiment design"
date: 2020-03-05
---

As shown below, I would take the KDD99 dataset and the NSL-KDD dataset, split the data into test and training sets, and train a set of machine learning algorithms. Using the test set I can calculate precision, recall, and the F1 score. These results I can compare to a second set of algorithms trained from pcap datasets.

CTU-13, CICIDS2017, and NIDS-AML would have to undergo preprocessing as they are in their base .pcap forms. According to Sharafaldin et al, they were able to pull 80 features from their pcaps (I'm currently trying to reach the site to get this but it seems to be down http://205.174.165.80/CICDataset/CIC-IDS-2017/). This can then train the same set of algorithms before also determining precision, recall, and the F1 score.

Not shown here: exploratory analysis of the human-generated data. Needs to be evaluated for temporal artifacts and correlated with any strategy declared in the interview. 

<img src="/assets/030520.png" width="1000">
