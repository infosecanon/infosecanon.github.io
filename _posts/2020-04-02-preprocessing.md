---
layout: post
title: "Preprocessing"
date: 2020-04-02
---

# Preprocessing
We need to preprocess the network traffic such that 1) it's normalized, 2) roughly the same size, 3) representative of the larger datasets.

and hopefully 4) it's somewhat balanced (probably wishful thinking).
Smaller sample files give me the opportunity to build the rest of the pipeline without losing a ton of time in training.

## Installing and Running CICFlowMeter
I went to the Github repo referred by Dr. Sharafaldin:
https://github.com/ahlashkari/CICFlowMeter

Needed to install the following dependencies on Ubuntu 18.04
```
root@ubuntu:~/AML/CICFlowMeter/jnetpcap/linux/jnetpcap-1.4.r1425# apt install gradle
```

```
datasci@ubuntu:~/AML/CICFlowMeter/jnetpcap/linux/jnetpcap-1.4.r1425$ sudo apt install maven
```

## Installing with Maven
```
root@ubuntu:~/AML/CICFlowMeter/jnetpcap/linux/jnetpcap-1.4.r1425# mvn install:install-file -Dfile=jnetpcap.jar -DgroupId=org.jnetpcap -DartifactId=jnetpcap -Dversion=1.4.1 -Dpackaging=jar
```

## Running with Gradle
```
root@ubuntu:~/AML/CICFlowMeter/jnetpcap# cd ..
root@ubuntu:~/AML/CICFlowMeter# ls
build.gradle gradlew jnetpcap pom.xml ReadMe.txt src
gradle gradlew.bat LICENSE.txt README.md settings.gradle
root@ubuntu:~/AML/CICFlowMeter# gradle execute
```

Cool! It should be installed and working. The UI looks like:
<img src="/assets/CICFlowMeter.png" width="700">

Some other notes:

The NIDS-AML set is saved in `.pcapng` and needed to be converted to `.pcap`. This was completed using:
```
$ tshark -F pcap -r P1_dvwa_101619.pcapng -w P1_dvwa_101619.pcap
```

Some of these pcaps are huge (8GB+) a piece. To chunk these down I'm using editcap, part of wireshark:
```
$ editcap -c 100000 Friday-WorkingHours.pcap friout.pcap
```

It remains to be seen if the packets lost via chunking make a difference in training...

Now we have three processed (tiny) CSVs to work with from each dataset - CTU13, NIDS-AML, and CICIDS2017 - each with the same number of features. We still need to label and reduce the feature space of the categorical variables.

<a href="/assets/P1_dvwa_101619.csv">NIDS-AML</a>
<a href="/assets/friout_00095_20170707131431.csv">CICIDS2017</a>
<a href="/assets/botnet-capture-20110810-neris.csv">CTU-13</a>
