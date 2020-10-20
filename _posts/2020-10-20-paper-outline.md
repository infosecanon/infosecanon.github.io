---
layout: post
title: "Paper Outline"
date: 2020-10-20
---
# Diagram

[WIP CICIDS17](/assets/CICIDS17-EDA-RF-101720.html)

# Outline

1. Introduction
  - Current network intrusion detection paradigm
  - Anomaly-based vs. signature-based and hybrid
  - Discuss problems with datasets and recent trends
  - Network traffic capture storage objects (pcap vs netflow)
        - and the features of each
        - pros vs. cons
  - Anomaly detection algorithms, the datasets they used
  - Our contributions:
        - An analysis of the features from 3 different, publicly available, network intrusion datasets, comprising over 80 GB of raw network data. This analysis compares the reviewed datasets on metrics such as size, protocol diversity, and feature importance.
        - A new dataset that, to our knowledge, is the first collection to provide labelled, IRB-cleared, benign and attacker data that is publicly available.
        - Analysis of human-generated attack traffic and automatically-generated attack traffic to determine the differences that exist between them at a feature level.
        - An evaluation of classifier-agnostic feature importance across the datasets. As not all features are equally important, we evaluate 80 features, determine feature ranking, and draw conclusions about which features are not important across datasets and network topologies thus saving compute power.
        - Metrics on the performance increase across algorithms by eliminating these features.

2. Related Work
    - Related datasets
        - KDD
        - NSL-KDD
        - There are many, many more
    - Network infrastructure projects
        - PlanetLab
        - Fabric Testbed
        - Geni.net
    - How other projects have preprocessed their datasets
    - How other projects have performed feature selection for ML

3. Dataset Review
  - CTU-13
  - CICIDS17
  - NIDS-AML / NIDS-Human

4. Preprocessing & Labelling
  - CICFlowMeter and features, what they mean
  - Labelling CTU-13
  - Labelling CICIDS17
  - Labelling NIDS-AML

5. Dataset Feature Importance Comparison
  - Values with zero or near-zero variance
  - Why 0s are 0s from a network SME perspective
  - Feature selection with RF
  - Remaining Features

6. Optimization Metrics

7. Future Work
8. Conclusion
9. Acknowledgments
10. Availability (Dataset repo location)
11. Bibliography
12. Appendix A - Pentester Interviews
