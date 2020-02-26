---
layout: post
title: "dataset comparisons"
date: 2020-02-25
---

Recap
---------
- [ ] We need to show a stronger comparison against prior work
- [ ] Show how the dataset is used in practice
- [ ] Show a comparison against other datasets - be specific about the feature differences and where they come from 
- [ ] Adjust the tone of the paper to be easier to follow (stop going from technical to high level)
- [ ] More detail on surfing from users 
- [ ] Justify the false positive / false negative argument 
- [x] Conferences identified: SecureComm (due 5/4/2020) and ACSAC (due 6/15/2020)
- [x] Defend why we used TLS 1.2 over TLS 1.3



## Dataset Comparisons and prior work
- [x] We need to show a stronger comparison against prior work

What are some other dataset papers and where were they published from?

Title                  | First author | Conference                       | Year 
-----------------------|--------------|----------------------------------|--------
Intrusion Detection in 802.11 Networks: Empirical Evaluation of Threats and a Public Dataset | Kolias | IEEE Communication Surveys & tutorials 1st quarter | 2016
UNSW-NB15: A Comprehensive Data set for Network Intrusion Detection Systems | Moustafa | Military Communications and Information Systems Conference (MilCIS) | 2015
SSH Compromise Detection using NetFlow/IPFIX | Hofstede | ACM SIGCOMM Computer Communication Review | 2014
An empirical comparison of botnet detection methods | Garcia | Elsevier Computers & Security 45 | 2014
UGR‘16: A new dataset for the evaluation of cyclostationarity-based network IDSs | Maciá-Fernández | Elsevier Computers & Security 45 | 2014
Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization | Sharafaldin | International Conference on Information Systems Security and Privacy | 2018
Unified Host and Network Data Set | Turcotte | arxiv | 2017
Toward a reliable anomaly-based intrusion detection in real-world environments | Viegas | Elsevier Computer Networks 127|2017
Detecting P2P botnets through network behavior analysis and machine learning | Saad | Ninth Annual International Conference on Privacy, Security and Trust | 2011

Most of these are journals which have longer review/publish cycles. 

Seen another way, a thorough survey is provided by Ring et al. 



### KDD99 Dataset - The Archetype
The KDD99 dataset is considered the prototypical dataset with over a hundred citations. 

Reference: [KDD99 Data Location](https://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html)
Reference: [KDD99 Description](http://kdd.ics.uci.edu/databases/kddcup99/task.html)
Reference: [Problems with the KDD99 Dataset](https://www.kdnuggets.com/news/2007/n18/4i.html)

### NSL-KDD Dataset - The Improvement
From *A Detailed Analysis of the KDD CUP 99 Data Set*, Tavallaee, et al.
> The NSL-KDD data set has the following advantages over the original KDD data set:
> * It does not include redundant records in the train set, so the classifiers will not be biased towards more frequent records.
> * There is no duplicate records in the proposed test sets; therefore, the performance of the learners are not biased by the methods which have better detection rates on the frequent records.
> * The number of selected records from each difficulty level group is inversely proportional to the percentage of records in the original KDD data set. As a result, the classification rates of distinct machine learning methods vary in a wider range, which makes it more efficient to have an accurate evaluation of different learning techniques.
> * The number of records in the train and test sets are reasonable, which makes it affordable to run the experiments on the complete set without the need to randomly select a small portion. Consequently, evaluation results of different research works will be consistent and comparable.

Reference: [NSL-KDD Data location](https://github.com/jmnwong/NSL-KDD-Dataset)
Reference: [NSL-KDD Description](https://www.unb.ca/cic/datasets/nsl.html)

### CTU-13


### CICIDS 2017
