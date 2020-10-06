---
layout: post
title: "Literature Review"
date: 2020-09-22
---
# Literature Review

We're far enough along now that it makes sense to begin writing the paper to
collect the research so far. The beginning of this post is raw analysis while a
summary is available towards the end.

- [Methodology](#methodology)
  * [Google Scholar](#google-scholar)
    + [Efficient IoT-based sensor BIG Data collection-processing and analysis in smart buildings](#efficient-iot-based-sensor-big-data-collection-processing-and-analysis-in-smart-buildings)
    + [Botnet Detection via mining of network traffic flow](#botnet-detection-via-mining-of-network-traffic-flow)
    + [Towards Large Scale Packet Capture and Network Flow Analysis on Hadoop](#towards-large-scale-packet-capture-and-network-flow-analysis-on-hadoop)
    + [A Systematic Review of Defensive and Offensive Cybersecurity with Machine Learning](#a-systematic-review-of-defensive-and-offensive-cybersecurity-with-machine-learning)
    + [DeepDCA Novel Network-Based Detection of IoT Attacks Using Artificial Immune System](#deepdca-novel-network-based-detection-of-iot-attacks-using-artificial-immune-system)
    + [Towards Large Scale Packet Capture and Network Flow Analysis on Hadoop](#towards-large-scale-packet-capture-and-network-flow-analysis-on-hadoop-1)
    + [Building an Effective Intrusion Detection System Using the Modified Density Peak Clustering Algorithm and Deep Belief Networks](#building-an-effective-intrusion-detection-system-using-the-modified-density-peak-clustering-algorithm-and-deep-belief-networks)
    + [Packet2Vec: Utilizing Word2Vec for Feature Extraction in Packet Data](#packet2vec--utilizing-word2vec-for-feature-extraction-in-packet-data)
    + [Stub](#stub)
    + [Stub](#stub-1)
    + [Stub](#stub-2)
  * [IEEE Xplore](#ieee-xplore)
  * [ACM Digital Library](#acm-digital-library)
- [Papers of Interest](#papers-of-interest)
- [References of Papers of Interest](#references-of-papers-of-interest)

We're looking for information that will
* Provide datasets, algorithms, and/or metrics commonly used to validate results in this space
* Discuss how preprocessing was performed such that we can compare to our method
* Provides context for where the research space is


Currently our pipeline looks like this:

<img src="/assets/pipeline.png" width="450">


The datasets we have analyzed this way include:

<img src="/assets/datasets.png" width="600">


Experimentally, this could be our set up:

<img src="/assets/exp-comp.png" width="600">



CICIDS2017, broken down, looks like this:

<img src="/assets/cicids2017-grey.png" width="600">




# Methodology
I needed to gather and evaluate related work for the paper, thus needing to
search for a corpus. Searches using Google Scholar, IEEE Xplore, and ACM Digital
 Library should suffice. With the broader search complete, review then becomes a
 task of determining key work and chasing down _their_ references.

## Google Scholar
This first set of papers was gathered using a Google scholar search for
`pcap processing -genome` (turns out there's a 'pcap' match in bioinformatics)
and going through the first 10 pages of results.

The idea behind the search term was to draw conclusions on the body of research
where machine learning is applied to cybersecurity, particularly network
intrusion detection. In that niche we needed to know how researchers are
pre-processing their data and performing feature selection.

What follows are notes on the papers gathered.

### Efficient IoT-based sensor BIG Data collection-processing and analysis in smart buildings

Authors: Plageras, A., Psannis, K., Stergiou, C., Wang, H., Gupta, B.
Published in: Elsevier - Future Generation Computer Systems

* This is more a 'smart building' paper without a security context
* Simulations using Contiki OS and Cooja
* Contains several nodes with different building management protocols like IEEE
802.15.4, IPv6, 6LoWPAN, CoAP
* Saved traffic data using pcap...but doesn't say where to get the data. Request?


### Botnet Detection via mining of network traffic flow

Authors: Mathur, L., Raheja, M., Ahlawat, P.
Published in: International Conference on Computational Intelligence and Data
Science (ICCIDS 2018)

* Examines the packet header
* Spider the related work -> seems there is a base of botnet detection research that
we might be able to lean on

* VMWare, nfdump/nfcapd to collect network traffic
* USES CTU-13 DATA and ISOT Dataset (?)
* Doesn't really discuss the network they gathered traffic on

...oh my:

>The data recorded using virtual machines and the data downloaded from external
sources was too large to be processed using normal desktop or laptop machines.
Hence to overcome that hurdle, a small but sizable chunk of data was randomly
selected which could be processed with the available machines in a practical
amount of time. The selection of data was entirely random to ensure that the
results of the analysis remain unbiased by any editing or selective choosing.

So it looks like here they randomly selected a subset of the data and performed
analysis on that due to hardware limitations.


Algorithms evaluated:
* Randomized Filtered Classifier
* Logistic Regression
* Random Committee
* Random Subspace
* Multi Class Classifier

Attributes used:
* Ts (Flow start time)
* Te (Flow end time)
* Td (Flow duration)
* Sa (Source IP address)
* Da (Destination IP address)
* Sp (Source port)
* Dp (Destination port)
* Pr (Protocol)
* Ra/flg (Flg Flags)
* Ipkt (Input Packets)
* ibyt (Input Bytes).


In this paper, `CfsSubsetEval` was used to perform feature selection.
>CfsSubsetEval attribute evaluator was used in conjunction with a best first
search method which resulted in the following subset: td(Flow duration),
da(destination address), pr(protocol).

They used the metrics of 1) Accuracy and 2) Time Taken (to build and eval the
  training set)

To note, they grabbed a random subset of the overall data but don't provide the
data they collected so it's nigh impossible to reproduce or beat their numbers.

They don't talk about how much data each algorithm was trained on which can
affect the accuracy.


### Towards Large Scale Packet Capture and Network Flow Analysis on Hadoop

Authors: Zenon, M., Saavedra, N., Emmanuel, W., Yu, S.
Published in: 2018 Sixth International Symposium on Computing and Networking
Workshops

* Proposes the `hcap` framework over the `hadoop-pcap` library resulting in
performance improvements

Interesting note:
>The PCAP file format, however, was never intended to be used in heavy
processing, making it challenging to incorporate it into Hadoop [6], [14].

* Not applicable to our research


### A Systematic Review of Defensive and Offensive Cybersecurity with Machine Learning

Authors: Aiyanyo, I., Samuel, H., Lim, H.
Published in: Applied Sciences doi:10.3390/app10175811

* Very methodical
* Evaluated over 1700 records -> 120 ML/Cyber papers

Some good quotes from the paper:
>ML techniques are evaluated using standard metrics such as true positive rate,
false positive rate, accuracy, precision, recall, F1 score, false alarm rate,
and confusion matrix.

Sounds like good metrics to evaluate our work with, though `false positive rate`
and `false alarm rate` seem like the same thing to me.

>We identified seven commonly used classification techniques in the selected
reviewed papers on IDS, a defensive cybersecurity strategy: Support Vector
Machine (SVM), Naive Bayes, Decision Trees, Random Forests, Logistic Regression,
 Neural Networks, and hybrid methods.

* Hybrid (combining signature-based and anomaly-based detection methods) is, by
far and away, the most popular. Followed by SVM and NB, respectively.

On commonly used datasets:

>KDDCUP’99 was the most commonly used data set in the selected reviewed papers
and this was followed by DARPA’99, NSL-KDD, log files, and honeypot. In Figure 5,
 the list of others includes MiniChallenge2, PREDICT, ADFA-LD, UCI, USPS,
 CDMC2012, SEA, CSIC2010, SSNET2011, ISCX, NIST, ISOT, HIGGS1, SUSY2, Collection,
  Flower, NAB, MUTAG, ENZYMES, Tiki Usenet, CIDDS-001, Netresec AB 2015, RTBTE,
CAIDA’07, and CAIDA’08.

Now, some of these I've never even _heard_ of and I've read two decent survey
papers solely concentrating on NIDS datasets. This paper seems worth keeping to
dig into the resources.

Note that some of these datasets also include 'enriched' data from logs that
can't be obtained without that network element. That is, if ex_dataset_1 has
'enriched' data with logs, etc and ex_dataset_2 does not, there are fields that
go unfilled in the event `UNION {ex_dataset_1, ex_dataset_2}`

Attacks studied in order of prevalence:
* DoS
* User to Root
* Remote to Local
* Probing
* Phishing
* SQLi
* Recon

One of the key insights:

>4.1. High Dimensionality of Network Traffic Data
High dimensionality of network traffic data has made classification challenging
as network traffic data usually comprise of many attributes and features [39].
This is mainly due to the computational complexity and resources required to
process large and sparse matrices with many feature columns and observation
rows. This challenge makes it difficult for researchers to train models in order
 to differentiate between anomalous and normal behavior [40]. As a result, many
 of the selected reviewed papers discussed the need for a reduction in the
 dimensionality of network traffic data as well as feature selection and the
 introduction of ML techniques when classifying such data. Some of the authors
 of the selected reviewed papers employed data mining techniques in a cloud-based
  environment, by choosing suitable attributes and features with the least
  relevance with regards to weight for the classification. In the majority of
  the reviewed studies, the standard strategy is to choose features with more
desirable weights.


### DeepDCA Novel Network-Based Detection of IoT Attacks Using Artificial Immune System

Authors: Aldhaheri, S., et al
Published in: Applied Sciences doi:10.3390/app10061909

Uses hybrid Deep Learning and Dendritic Cell Algorithm (Deep DCA) to classify
IoT traffic and minimize false alarm generation

Seem to have written their own preprocessing?

Technology stack cited as follows:
>Moreover, for data exploration and visualization we used ggplot framework [72]
and Seaborn [73]. For preprocessing steps and feature engineering, Pandas
framework [74] and Numpy framework [75] have been used. To calculate performance
 metrics, scikit-learn [76] was used, and finally, for data analysis,
 scikit-learn framework and Keras [77] were used.

So it would appear they are using mostly the same frameworks (scikit-learn, numpy,
  pandas).

Uses the BoT-IoT dataset [79]:

>created in the Cyber Range Lab of The center of UNSW Canberra Cyber and has
more than 72,000,000 records which include DDoS, DoS, OS and Service Scan,
Keylogging and Data exfiltration attacks

Has a really nice metrics table for dataset statistics containing:

- Name
- Rows
- Columns
- Discrete Columns
- Continuous Columns
- All missing Columns
- Missing observations
- Complete Rows
- Memory allocation

Table 4 has a frequency distribution table of considered features - basically a
table breakdown of different attack types and the frequency in the dataset.

Figure 5 shows the Information Gain feature results.

>The features (‘seq’, ‘DstIP’, ‘srate’, ‘SrcIP’, ‘max’), are the most
discriminative attribute. While the rest (‘mean’, ‘stddev’, ‘min’,
‘state_number’, ‘drate’) have small maximum information gain (smaller than 0.5),
 which little contribute to intrusion detection.

Table 9 Shows their strange classifier's performance to performances of KNN, NB,
 SVM, and MLP.

We could use this to compare to ours if we had their dataset...




### Towards Large Scale Packet Capture and Network Flow Analysis on Hadoop

Authors: A Deep Learning Ensemble for Network Anomaly and Cyber-Attack Detection
Published in: Dutta, V., Choras, M., Pawlicki, M., Kozik, R.

On Feature Selection:
>NetFlow datasets often include non-identical feature attributes that are
categorized as flow, basic, content, time, additionally generated, and labeled
features, respectively. However, the information gathered from packet captures
also provides a variety of irrelevant or redundant details. Removing unnecessary
 information offers better, unbiased detection. In addition to the above
 pre-processing, the selected datasets (i.e., IoT-23, LITNET-2020, NetML-2020)
 contain a certain amount of unusable values. Feature imputation was performed
 to replace the infinities with max values. For missing records, the feature
 means were used.

* Used data balancing techniques Synthetic Over-sampleing Technique (SMOTE) and
Edited Nearest Neighbors (SNN)

* Used Deep Sparse AutoEncoder (DSAE) to reduce feature space over PCA

* Fig 2: neat dataset viz

* Uses two different deep learning algorithms (Deep Neural Network (DNN),
Long Short-Term Memory (LSTM)) and a meta-classifier (Logistic Regression)

* LITNET-2020 (https://dataset.litnet.lt/data.php) - NETFLOWS only

> The data preprocessor selects initially 49 features that are specified to the
NetFlow V9 protocol [30] to arrange the dataset. Furthermore, an additional 15
feature attributes are supplemented by the data extender. Having said that, an
additional 19 attributes are offered to recognize attack types. Therefore, the
final datasets have a set of 84 feature attributes.

    * In table 7 however it appears that features 65-84 are sparse categorical flags?

* NetML-2020
https://github.com/ACANETS/NetML-Competition2020
https://www.stratosphereips.org/datasets-overview

    * Appears to have pcaps

    * Also used CICIDS2017

    * pcap -> json

    * Has 3 levels of granularity of detection (which is where the additional
  features come from)


* Table 10: Performance evaluation using RF, DNN, LSTM, and their stacked
proposed method using LITNET-2020

* Table 11: Evaluation metrics table including Precision, Recall, FPR, F1, MCC
using LITNET-2020

* Table 12: Performance evaluation using RF, DNN, LSTM, and their stacked
proposed method using NetML-2020

* Table 13: Evaluation metrics table including Precision, Recall, FPR, F1,
MCC using NetML-2020

* Figure 4 has a graph of training time

Datasets used:
* IoT-23: https://www.stratosphereips.org/datasets-iot23
* LITNET-2020: https://dataset.litnet.lt
* NetML-2020: https://github.com/ACANETS



### Building an Effective Intrusion Detection System Using the Modified Density Peak Clustering Algorithm and Deep Belief Networks

Authors: Yang, Y. et al

Published in: Applied Sciences doi:10.3390/app9020238
https://www.mdpi.com/journal/applsci (it's a pay-for-play journal, ick)

* Fuzzy aggregation IDS approach using the modified density peak clustering
algorithm (MDPCA) and deep belief networks (DBNs)


* MDPCA is used to divide the training set into several subsets with similar
sets of attributes to reduce the size of the training set and the imbalance of
the samples

* Uses NSL-KDD and UNSW-NB15 datasets

* Metrics: accuracy, recall, precision and F1-score


Interesting note about feature space inflation:
>the NSL-KDD [21,22] dataset contains 3 symbol features and 38 numeric features,
 and the UNSW-NB15 [25,26] dataset contains 3 symbol features and 39 numeric
 features. Symbol features in the NSL-KDD dataset include protocol types (e.g.,
 TCP, UDP, and ICMP), destination network services (e.g., HTTP, SSH, FTP, etc.)
 and normal or error status of the connection (e.g., OTH, REJ, S0, etc.). In the
  proposed model, the original training dataset is divided into several subsets
  using the MDPCA clustering algorithm. To avoid the influence of the discrete
  attributes on clustering, these symbol features are encoded using a one-hot
  encoding scheme. For example, the symbol feature “protocol type” in the
  NSL-KDD dataset has three discrete values, namely TCP, UDP, and ICMP, which
can be encoded in a space of three dimensions (with one-hot feature vectors
[0, 0, 1], [0, 1, 0], and [1, 0, 0]). Since the symbol features “service types”
and “flag types” in the NSL-KDD dataset include 70 and 11 discrete attributes,
respectively, they can be transformed to 70 and 11 one-hot feature values,
respectively. According to this method, the 41-dimensional original features of
 the NSL-KDD dataset are finally transformed into 122-dimensional features.
Similarly, the 42-dimensional features in the UNSW-NB15 dataset are converted
to 196-dimensional features.

* Compared against (Tables 10, 12):
    * K-Nearest Neighbor (KNN)
    * Multinomial Naive Bayes (MultinomialNB)
    * Random Forest (RF)
    * Support Vector Machine (SVM)
    * Artificial Neural Network (ANN)
    * Deep Belief Network (DBN)

### Packet2Vec: Utilizing Word2Vec for Feature Extraction in Packet Data

Authors: Eric L. Goodman, Chase Zimmerman, and Corey Hudson
Published in: Sandia National Laboratories, Albuquerque, NM, USA; arXiv

* Applies Word2Vec to packet data for automatic feature extraction






















### Stub

Authors:
Published in:



### Stub

Authors:
Published in:



### Stub

Authors:
Published in:












## IEEE Xplore

On IEEE Xplore I used "network intrusion machine learning" as my search term
and went through the first 5 pages (1,621 results returned; went through the
  first 150).

### A Review of Machine Learning Methodologies for Network Intrusion Detection

  Authors: Phadke, et al
  Published in: Proceedings of the Third International Conference on Computing Methodologies and Communication (ICCMC 2019)

  - Discusses different ML approaches (SVM, 'algorithm proposed', k-means, ANN, NN)
  - Only analysis is across accuracy, FPR, and dataset (includes KDD99 cup papers)
  - Does not discuss data preprocessing

### Network Intrusion Detection using Supervised Machine Learning Technique with Feature Selection

    Authors: Taher, K., Jisan, B., Rahman, M.
    Published in: 2019 International Conference on Robotics,Electrical and Signal Processing Techniques (ICREST)

  a key paragraph:
  >The major challenges in evaluating performance of network IDS is the
  unavailability of a comprehensive network based data set [13]. Most of the
  proposed anomaly based techniques found in the literature were evaluated
  using KDD CUP 99 dataset [14]. In this paper we used SVM and ANN –two machine
  learning techniques, on NSL- KDD [15] which is a popular benchmark dataset for
  network intrusion.

  - so they used SVM and ANN to analyze the NSL-KDD (25,191 labeled instances) dataset.
  - Used Weka for analysis
  - 35 features

### MACHINE LEARNING BASED INTRUSION DETECTION SYSTEM

    Authors: Anish, A., Sundarakantham, K.
    Published in: Proceedings of the Third International Conference on Trends in Electronics and Informatics (ICOEI 2019)

  - NSL-KDD and UNSW-NB15
  - AdaBoost algorithms and Artificial Bee Colony compared against NB, SVM
  - Dataset is processed in Weka using Randomize
  - CfsSubsetEval used for feature reduction
  - Accuracy and misclassification rate are metrics

### Comparison Deep Learning Method to Traditional Methods Using for Network Intrusion Detection

    Authors: Dong, B., Wang, X.
    Published in: 2016 8th IEEE International Conference on Communication Software and Networks

  - Uses KDD-99 dataset
  - Synthetic Minority Over- Sampling Technique (SMOTE) to deal with unbalanced dataset
  - Precision evaluated on SVM with and without SMOTE

### USING INCREMENTAL LEARNING METHOD FOR ADAPTIVE NETWORK INTRUSION DETECTION

    Authors: Yang, W., Yun, X., Zhang, L.
    Published in: Proceedings of the Fourth International Conference on Machine Learning and Cybernetics, Guangzhou, 18-21 August 2005

  - Uses KDD-99 dataset
  - incremental efficient intrusion detection self-learning algorithm (IEIDSLA)
  which improves on DT learners like ID3
  - Metrics: detecting rate and detecting time

### On the Feasibility of Deep Learning in Sensor Network Intrusion Detection

    Authors: Otoum, S., Kantarci, B., Mouftah, H.
    Published in: IEEE NETWORKING LETTERS, VOL. 1, NO. 2, JUNE 2019

  - restricted Boltzmann machine-based clustered IDS (RBC-IDS) vs. adaptively
  supervised and clustered hybrid IDS (ASCH-IDS)
  - Metrics: accuracy, detection rate, FNR, ROC curves, F1 score curve

### Performance Comparison of Intrusion Detection System Between Deep Belief Network (DBN) Algorithm and State Preserving Extreme Learning Machine (SPELM) Algorithm

    Authors: Singh, K., Mathai, K.
    Published in: ??? Copyright 2019 IEEE

  - NSL-KDD Dataset
  - State Preserving Extreme Learning Machine(SPELM) vs. Deep Belief Network (DBN)
  - Accuracy, Precision, Recall, confusion matrix, execution time


















## ACM Digital Library

On ACM Digital Library I used "network intrusion machine learning" as my search
term and went through the first 2 pages before modifying search terms because I
had 449,107 results.

Modifying the search to "intrusion detection" | "machine learning" | "pcap" "preprocessing"
only whittled the results down to 111,485.










# Papers of Interest

# References of Papers of Interest
