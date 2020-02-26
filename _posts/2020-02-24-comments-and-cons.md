---
layout: post
title: "conferences and tls vulnerabilities"
date: 2020-02-24
---

# Initial Submission
We were provided the following USENIX comments:

## Reviewer 1

Strengths
----------
 * Diversity of attacks captured
 * Traffic is from live users, not simulations

Weaknesses
----------
 * Artificial constraint requiring unencrypted data
 * No comparison of this data to prior work
 * No indication of how the data might be used in practice, especially with regard to adversarial ML

Detailed comments for authors
-----------------------------
I was excited to see this paper, as good datasets for ML benchmarking and experimentation are hard to find.  The authors did an excellent job setting up their network and creating the raw data, using volunteers to produce benign and attack traffic.  The features collected are reasonable and could serve as a starting point for further studies.

My main complaint about the data collection is that the authors artificially imposed a requirement that the data be in cleartext, and did a lot of engineering to downgrade TLS 1.3 connections to TLS 1.2.  This choice means that the data collected diverges sharply from real-life data, and there's no indication that the insights gleaned from the dataset in the paper will apply to real life.

Assuming we can justify this choice for data collection, the data set is great -- but the paper ends 5 pages early.  I would like to see the following:
- Analysis of how this data set compares to prior work.  Is your data set large or small?  You extracted 29 features (though I only see 20 in Table 3) -- is this a lot or a little?  Dataset [13] contains 49 features; why can't you get at least that many?  My concern is that the preprocessing you do removes a lot of information in the data, and your feature engineering may not capture everything that could be used in a model or attack.  When in doubt, err on the side of more raw data.
- Show how the data can be used in practice to study intrusion detection.  What insights can be gained from it?  What new techniques can be developed?  This paper has no impact until it is used to advance our knowledge.  The data set is a contribution in itself, so you don't need to have the best attack or defense ever, but you need to show that we can get *some* use out of it.

Finally, the data as collected has nothing to do with adversarial ML.  Either make this connection more concrete or remove the references.

Requested changes
-----------------
1. Collect data without removing TLS 1.3 traffic **and/or** show that the TLS 1.2 data you collected can be used to provide insights that apply to a more natural traffic distribution.
1. Show how your dataset improves on prior work.
1. Provide evidence that this dataset will be useful in practice.

## Reviewer 2

Strengths
---------
 * This paper addresses one the core needs of our community; the creation of labeled data appropriate for model validation.  Once vetted, such a data set may enabled lots of new an interesting research. 

 * The focus on creating network traffic that exhibits false positives and negatives is very intersting; exploring how trained models are vulnerable in an adaptive fashion seems like a good direction.

 * The integration/fusion of real users and synthetic traffic provides more realism in the data set.

 * Reading about the data processing pipeline was quite interesting.  I learned a few things about the joy tool that will be helpful in the future.

Weaknesses
----------
 * The challenge of this paper is that while it provides a service to the community (and a good one, I would argue), it is difficult to identify what new science resulted from the effort. See notes below for suggestions.

 * The process by which the authors trained models and how this was integrated into the data set was a bit hard to follow.  The authors should provide a good deal of detail on how you trained the models, what features were used, and the process by which retraining was performed.

 * The paper could use some more organization.  Right now, the paper jumps between very high level details and low level technical details.  As a result, the arc of the paper is sometimes hard to follow.

Detailed comments for authors
-----------------------------
remove reference to university for blind submissions 

Requested changes
-----------------
1. Could the authors provide a detailed argument of what new discovery this paper makes; perhaps some new methods for structuring or collecting trace data. Are there new processing techniques that one could take away from this paper?

1. Could you provide more detail on what exactly the users did to surf.  Was there a script and did everyone do the same thing at generally the same time?  And where do the set of tasks come from (user or traffic study)?

1. Can you justify more carefully what the approaches for data collection and user and automated traffic generation lead to more false positives?  Same for false negatives.

Questions for authors' response
-------------------------------
Can you clarify what you mean by, "Richer data, like full unencrypted network traffic payloads, is more functional for various use cases but requires more storage and processing capabilities"?  Is it the fact you are collecting payloads that requires more storage?

Summation
---------
- [ ] We need to show a stronger comparison against prior work
- [ ] Show how the dataset is used in practice
- [ ] Defend why we used TLS 1.2 over TLS 1.3
- [ ] Show a comparison against other datasets - be specific about the feature differences and where they come from 
- [ ] Adjust the tone of the paper to be easier to follow (stop going from technical to high level)
- [ ] More detail on surfing from users 
- [ ] Justify the false positive / false negative argument 


## Where to go next
An initial search of conferences that could be both appropriate for the content and timely led to this table:

Tier  | Abrev | Name | CFP | Date | Location     | Site
------|-------|------|-----|------|--------------|------------------------------------
2 | ESORICS | European Symposium on Research in Computer Security | | September 2020 (CFP not out yet) | N/A | http://conf.laas.fr/esorics/
2 | RAID | International Symposium on Recent Advances in Intrusion Detection | | September 2020 (CFP not out yet) | N/A | http://www.raid-symposium.org/
2 | ACSAC | Annual Computer Security Applications Conference | June 15, 2020 | December 7-11 2020 | Austin, TX | https://www.acsac.org
2	| DSN	| The International Conference on Dependable Systems and Networks	| Dec 13 2019	| June 29 - July 2 2020	| Valencia, Spain	| https://dsn2020.webs.upv.es/		
2	| ASIACCS	| ACM Symposium on Information, Computer and Communications Security | Dec 10 2019	| June 1-5, 2020	| Taipei, Taiwan	| https://asiaccs2020.cs.nthu.edu.tw/		
2	| PETS | Privacy Enhancing Technologies Symposium	Issue 4: | February 29, 2020 | July 14-18 2020	| Montreal, Canada	| https://petsymposium.org/cfp20.php		
2	| EuroS&P	| IEEE European Symposium on Security and Privacy	| November 20, 2019	| June 16-18 2020	| Genova, Italy	| http://www.ieee-security.org/TC/EuroSP2020/		
2	| CSF	| IEEE Computer Security Foundations Symposium | Feb 7 2020	| June 22-26 2020	| Boston, MA	| http://www.ieee-security.org/CSFWweb/		
3	| SecureComm | Internation Conference on Security and Privacy in Communication Networks	| May 4 2020	| October 21-23	| Washington DC	| http://securecomm.org/
3	| CNS	| IEEE Conference on Communications and Network Security	| Feb 9 2020	| "June 29 - July 1"	| Avignon, France	| https://cns2020.ieee-cns.org/		
3	| DIMVA	| GI SIG SIDAR Conference on Detection of Intrusions and Malware and Vulnerability Assessment	| Feb 19 2020	| June 24-26	| Lisbon, Portugal	| https://dimva2020.campus.ciencias.ulisboa.pt/dates.html		
3	| ACNS	| International Conference on Applied Cryptography and Network Security	| Jan 22 2020	| June 22-25	| Rome, Italy	| https://sites.google.com/di.uniroma1.it/ACNS2020		
3	| SOUPS	| Symposium On Usable Privacy and Security	| Feb 20 2020	| August 9-11 2020	| Boston, MA	| https://www.usenix.org/conference/soups2020		
3	| ICICS	| International Conference on Information and Communications Security	| | December 2020 (CFP not out yet)		

The two most appropriate conference were identified as SecureComm (acceptance rate of 28%(30/108) according to Guofei) and ACSAC with due dates of May 4th and June 15th, respectively. 	
