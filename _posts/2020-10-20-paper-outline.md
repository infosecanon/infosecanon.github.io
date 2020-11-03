---
layout: post
title: "Paper Outline"
date: 2020-10-20
---
# Diagram

[WIP CICIDS17](/assets/CICIDS17-EDA-RF-101720.html)

# Outline

1. Introduction
  - Current network intrusion detection paradigm; Anomaly-based vs. signature-based and hybrid

      As communication technologies used across the internet mature and the nature of devices attached to the internet are changing, it becomes paramount to maintain the security mechanisms used to protect private infrastructure connected to public domain. Network intrusion detection systems (NIDS), one of the tools in the security toolset, leverages different techniques to detect malicious traffic. Signature-based solutions, such as Snort, rely on a database of indicators of compromise (IOCs) to detect attacks. This technique allows defenders to share IOCs across organizations but is unable to detect attacks never seen before, or zero day attacks. Anomaly-based detection, by comparison, relies on encoding features from network traffic and applying statistical and/or machine learning techniques to detect attacks. The anomaly-based technique suffers primarily through a high false positive rate that has been known to cause alert fatigue in defenders. Most modern solutions use both techniques.
  - Discuss problems with datasets and recent trends, Network traffic capture storage objects (pcap vs netflow)

      Anomaly-based NIDS research relies on datasets to improve state-of-the-art classifying techniques. The changing network traffic landscape requires that these datasets are formed using rigorous metrics and can be quickly outdated based on the traffic profile and attacks provided in the data. Usable network data, however, has been traditionally difficult to obtain {Sommer, amit2018machine, ring2017toolset}. Traditional issues with network intrusion detection research include: a lack of labeled data, datasets that are statistically imbalanced between anomalous and benign data, a lack of rigor in academic anomaly detection research that does not translate to operational validity, detection mechanisms that suffer from superfluous false positives at scale and incur nontrivial analyst overhead and eventual distrust {anderson2016identifying}, network data that cannot be released due to leaking network stakeholder information or violate user confidentiality {ring2019flow}, and using simulated data versus real data {Sommer}. Larger amounts of labelled network data are beneficial for machine learning but take longer to methodically label as benign or malicious. Automatic methods of labeling incur questions regarding the ground truth. Richer data, like full unencrypted network traffic payloads, is more functional for various use cases but requires more storage and processing capabilities. Netflow views of the same data can save on space and processing but feature visibility can be lost and the original traffic cannot be reconstructed {ring2019flow}.

  - Anomaly detection algorithms - 3 paragraphs
          - discusses how the state-of-the-art evolved
          - dataset used; pcap or netflow
          - features used
          - how they were selected if indicated

  - Our contributions:

- An analysis of the features from 3 different, publicly available, network intrusion datasets, comprising over 80 GB of raw network data. This analysis compares the reviewed datasets on metrics such as size, protocol diversity, and feature importance.
- A new dataset that, to our knowledge, is the first collection to provide labelled, IRB-cleared, benign and attacker data that is publicly available.
- Analysis of human-generated attack traffic and automatically-generated attack traffic to determine the differences that exist between them at a feature level.
- An evaluation of classifier-agnostic feature importance across the datasets. As not all features are equally important, we evaluate 80 features, determine feature ranking, and draw conclusions about which features are not important across datasets and network topologies thus saving compute power. Subject matter expertise, not merely statistical significance, is applied to
- Metrics on the performance increase across algorithms by eliminating these features.

    - Paragraph on navigating the paper

2. Related Work
    - Related datasets
        - KDD
        Previous datasets in this area include packet traces from DARPA/Lincoln Labs and the KDD dataset derived from those traces. The DARPA/Lincoln Labs packet traces resulted from monitoring a simulated Air Force network for weeks {lippman99}. This data was gathered in 1998 and refined in 1999. The KDD dataset distills the network traffic and adds labels for machine learning {kd99}. Neither of these datasets, both simulated, reflect current attack techniques or methodologies {Sommer} and due to their simulated nature they also do not contain real packet headers or payload data. Intrusion detection research data studied by private enterprise often carries data confidentiality risks where sensitive network implementation details could be inadvertently leaked {blake}.
        - NSL-KDD
        - There are many, many more
    - Network infrastructure projects - 1 paragraph
        - PlanetLab
        - Fabric Testbed
        - Geni.net
    - How other projects have preprocessed their datasets - 1 paragraph
    - How other projects have performed feature selection for ML - 1 paragraph

3. Dataset Review
  - 1 paragraph on why we used these datasets
  - As netflows can irreversibly convert a pcap and we wished to preserve a data structure that is most usable for further research, we prioritized datasets in the pcap format that were publicly available. We chose datasets that exhibited different types of attack traffic over a range of network topologies. Further, the datasets only contained actual traffic and not traffic generated by an algorithm. Lastly, the dataset had to labeled to provide ground truth.

  - We wanted to analyze this data to answer two questions:
      * Was there a pattern of usable features across topologies that is algorithm agnostic?
      * Were there discernible differences between attack traffic initiated from a tool and from a live attacker at the feature level?

  - A pattern of usable features across topologies reduces the amount of compute time and storage space required for defenders to train network intrusion detection algorithms. Few discernible differences between tool-generated attack data and human-generated attack data supports further development in adversarial emulation using tool-generated data as it is cheaper and faster to generate that way.

  - CTU-13
      - 1 paragraph explanation of the dataset and about the network it was captured on
      - The CTU-13 dataset {garcia2014empirical} comprises of thirteen network traffic captures with botnet traffic. The network consisted of virtualized computers running Windows XP SP2, what the botnet malware could run on at the time, on a Linux Debian host bridged into the university network. The final set contains both the traffic from the virtualized computers and the university router though some of the traffic was removed due to privacy concerns. The authors distinguished botnet traffic as traffic that travels to or from any known infected IP addresses.
      - Maybe some words about features? distribution? protocol variety?
      - Maybe attack:benign ratio? how large is the dataset?
  - CICIDS17
      - 1 paragraph explanation of the dataset and about the network it was captured on
      - The CICIDS2017 dataset {sharafaldin2018toward} includes a variety of attacks including password brute forcing, a heartbleed exploit, botnet traffic, traffic floods resulting in denial of service and distributed denial of service, a web server SQL injection, cross site scripting, and an infiltration. These attacks are recorded on a diverse network consisting of Windows and Ubuntu hosts, a firewall, several switches, and using both Windows 8.1 and Kali as attacking nodes.
      - Maybe some words about features? distribution? protocol variety?
      - Maybe attack:benign ratio? how large is the dataset?
  - NIDS-AML / NIDS-Human
      - 1 paragraph explanation of the dataset and about the network it was captured on
      - The NIDS-AML dataset provided a large protocol variety by including services like an exchange server, DNS, an SMB fileshare, a wiki page, and a vulnerable web application (DVWA). Hosts included Windows 7 SP 2 and Ubuntu. Hosts were joined to an active directory server where baseline data was generated by scripting user actions via PowerShell. Each workstation was assigned to a specific user with a specific profile - either administration, engineering, or business. Each profile randomly browsed from a pool of 30 Azure-hosted websites using cUrl, emailed another user using the Exchange server, read or edited an SMB fileshare, or browsed to a pool of internal wiki pages. Baseline data consists of this profile-generated traffic, inter-endpoint traffic like ICMP, and traffic required to maintain network services like NTP. Automated attacks include reconnaissance techniques (like nmap, dig, nslookup, and DNS queries), web attacks (like directory traversals, password bruteforcing, and SQL injections), Layer 2 attacks using STP, botnet traffic via BoNeSi, and delivery of a payload.

      - We wished to obtain data that reflected both human interaction with the network and automated scripting to generate traffic. This same collection also contains malicious traffic captures of human attackers interacting with the network and the traffic of malicious tools used on the same network. We conducted semi-structured interviews with 10 ethical penetration testers in October 2019. The following subsections describe our recruitment process, candidate screening, and limitations. We argue that while it is not currently known how to connect a user's identity based on their network traces, progress is being made in this area {Neasbitt}, and to both protect the identities of the participants and release the data publicly, this study was evaluated and approved by our university's Institutional Review Board (IRB).

      - We advertised this research study to the following organizations to recruit participants: our local DEF CON group, our university's cybersecurity student organization, on virtual chatrooms (Slack) known to contain local cybersecurity professionals, university employees, and personal contacts. Employees, as they are potentially a vulnerable population, were specifically briefed that their participation was purely voluntary and refusal to participate would not affect their employment or any benefit to which they were already entitled.

      - We asked all volunteers to self-assess their abilities to complete tasks on the network. Specifically, we asked them to rate themselves from 1 to 5 on their ability to interact with services like a normal user and how proficient they were with finding and leveraging web application vulnerabilities. Participants were asked to keep notes of their strategy. For example, a strategy could have been using SQLi to determine a list of usernames and passwords. Responses are available in the repository listed in the Availability section.

      - While volunteers were asked to self-assess their abilities, and participants may inflate or deflate the perception of their skill sets based on how they wish the interviewer to perceive them {holbrook2003telephone}, we wanted a variety of skill levels available in the malicious data. We believe insider threats need not be seasoned penetration testers, and need only to know the threat exists, to leverage vulnerabilities using public resources.
      - Maybe some words about features? distribution? protocol variety?
      - Maybe attack:benign ratio? how large is the dataset?

  - 1 paragraph on the datasets we chose not to use and why


4. Preprocessing & Labeling
  - CICFlowMeter and features, what they mean
      - We used CICFlowmeter, previously known as ISCXFlowMeter {icissp16}, to process a raw pcap into features suitable for machine learning. CICFlowmeter provides 84 features from pcap as a csv. Other preprocessers, such as Joy {blake}, only provided 27 features.
      - Other papers that discuss pcap processing into features for ML
      - 1 large paragraph detailing feature processing across time
  - Labeling CTU-13
      - 1 paragraph explanation
  - Labeling CICIDS17
      - 1 paragraph explanation
  - Labeling NIDS-AML
      - 1 paragraph explanation

5. Dataset Feature Importance comparison
  - Evaluate 80 features, determine feature ranking, and draw conclusions about which features are not important across datasets
  - Values with zero or near-zero variance
  - Why 0s are 0s from a network SME perspective - is that feature important from a detection perspective?
  - Feature selection with RF
  - Remaining Features
  - 5 paragraphs

6. Optimization Metrics
  - Discussion about effects of feature selection on accuracy; why we chose the metrics we chose
  - 1 paragraph explanation
  - 1 graph with paragraph explanation

7. Future Work
  - We would like to curate an operational technology (OT) network dataset with serial and serial-over-Ethernet protocols for ICS-specific machine learning algorithms. The vast majority of datasets in this area focus on ISP-level or enterprise-level IT traffic. Few datasets are available with OT-specific protocols or hybrid networks containing a business enterprise network attached to a control system network. Participation was limited for this dataset and two specific improvements could be made with regards to increasing the level of participation. A virtual connection to the testbed available would have eliminated the requirement for the participant to be local or within traveling distance. Further, using a Capture the Flag event could provide more human factors data and provide additional insight to the strategies used across participants. A separate pcap per participant would aid in the manual labeling of data.

8. Conclusion
  - 1 paragraph
  - In this paper we have presented a means to optimize feature selection for anomaly-based NIDS validated by....promises and sparkles.
  - note that conference papers don't tend to have appendices

9. Acknowledgments
  - This work is supported by a grant from the Silicon Valley Foundation as an award through the Cisco Research Center. The authors would like to thank Chris Shenefiel, Blake Anderson, and the security professionals that donated their expertise to help make this research a success.

10. Availability (Dataset repo location)
  - Source code and further documentation are available: <repo here>

11. Bibliography
  - easily a page

# Timeline & Responsibilities

Parts of the paper remaining:

Related Work
- Anomaly detection algorithms - 3 paragraph
- Network infrastructure projects - 1 paragraph
- How other projects have preprocessed their datasets - 1 paragraph
- How other projects have performed feature selection for ML - 1 paragraph
- 1 paragraph on the datasets we chose not to use and why


Processing
- 1 large paragraph detailing feature processing across time
- 1 paragraph explanation Labeling CTU-13
- 1 paragraph explanation Labeling NIDS-AML
- 1 paragraph explanation Labeling CICIDS17

Dataset feature comparison
- 5 paragraphs

Optimization metrics
- 1 paragraph explanation
- 1 graph with paragraph explanation

Conclusion
- 1 paragraph

## Responsibilities
- Heather - Related Work, Processing  (11)
- Uchenna - Dataset feature comparison, Optimization metrics (7)
- Share conclusion (1)

## Timeline
Week of 11/3 - 11/9:
* Heather: 3 labeling paragraphs, 1 para network infra projects, 3 para anomaly detection algos
* Uchenna: work on feature extraction method

Week of 11/10 - 11/16:
* Heather: process an additional dataset? 3 para on related work
* Uchenna: process current datasets with method, begin feature comparison writeup

Week of 11/17 - 11/24:
* Heather: 1 para feature processing across time, 1 para conclusion, help with feature comparison
* Uchenna: 5 para feature comparison

Week of 12/1 - 12/7:
* Heather: Work on optimization metrics, begin paper review
* Uchenna: Work on optimization metrics, begin paper review

Week of 12/8 - 12/15:
* All: Paper adjustments




<div class="title">November 2020</div>
<table border="1">
<tbody><tr><th>Sun</th><th>Mon</th><th>Tue</th><th>Wed</th><th>Thu</th><th>Fri</th><th>Sat</th></tr>
<tr><td><span class="date">1</span></td><td><span class="date">2</span></td><td><span class="date">3</span></td><td><span class="date">4</span></td><td><span class="date">5</span></td><td><span class="date">6</span></td><td><span class="date">7</span></td></tr>
<tr><td><span class="date">8</span></td><td><span class="date">9</span></td><td><span class="date">10</span></td><td><span class="date">11</span></td><td><span class="date">12</span></td><td><span class="date">13</span></td><td><span class="date">14</span></td></tr>
<tr><td><span class="date">15</span></td><td><span class="date">16</span></td><td><span class="date">17</span></td><td><span class="date">18</span></td><td><span class="date">19</span></td><td><span class="date">20</span></td><td><span class="date">21</span></td></tr>
<tr><td><span class="date">22</span></td><td><span class="date">23</span></td><td><span class="date">24</span></td><td><span class="date">25 Turkey Day Break</span></td><td><span class="date">26 Turkey Day</span></td><td><span class="date">27 Black Friday</span></td><td><span class="date">28</span></td></tr>
<tr><td><span class="date">29</span></td><td><span class="date">30</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td></tr>
</tbody></table>
<p></p><div class="title">December 2020</div>
<table border="1">
<tbody><tr><th>Sun</th><th>Mon</th><th>Tue</th><th>Wed</th><th>Thu</th><th>Fri</th><th>Sat</th></tr>
<tr><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">1</span></td><td><span class="date">2</span></td><td><span class="date">3</span></td><td><span class="date">4</span></td><td><span class="date">5</span></td></tr>
<tr><td><span class="date">6</span></td><td><span class="date">7</span></td><td><span class="date">8</span></td><td><span class="date">9</span></td><td><span class="date">10</span></td><td><span class="date">11</span></td><td><span class="date">12</span></td></tr>
<tr><td><span class="date">13</span></td><td><span class="date">14</span></td><td><span class="date">15</span></td><td><span class="date">16</span></td><td><span class="date">17</span></td><td><span class="date">18</span></td><td><span class="date">19 Fall Semester Ends</span></td></tr>
<tr><td><span class="date">20</span></td><td><span class="date">21</span></td><td><span class="date">22</span></td><td><span class="date">23</span></td><td><span class="date">24 Xmas Eve</span></td><td><span class="date">25 Xmas Day</span></td><td><span class="date">26</span></td></tr>
<tr><td><span class="date">27</span></td><td><span class="date">28</span></td><td><span class="date">29</span></td><td><span class="date">30</span></td><td><span class="date">31 NYE</span></td><td><span class="date">&nbsp;</span></td><td><span class="date">&nbsp;</span></td></tr>
</tbody></table>
<p></p><div class="footer">
