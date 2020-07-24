---
layout: post
title: "moar queens"
date: 2020-07-24
---

We decided to add back the `Timestamp`, `Protocol`, and `Flow Bytes/s` / `Flow Packets/s` (without all the inf and NaNs). Thus, we had to reprocess the old flows into new queens.

Complete! [Reprocessing CICIDS](/assets/CICIDS-reprocess-072020.html)

Complete! [Reprocessing NIDS-Auto](/assets/NIDS-Auto-reprocess-072020.html)

Complete! [Reprocessing CTU-13](/assets/CTU-13-reprocess-072020.html)

IP [Reprocessing NIDS-Human](/assets/NIDS-Human-reprocess-072020.html)

Note: Having issues removing NaNs with `.dropna()`, might be a string?


[CTU-13 Boruta 072120](/assets/Boruta-CTU-13-072120.html)

Features in the green area: ['Src Port', 'Dst Port', 'Protocol', 'Timestamp', 'Total Fwd Packet', 'Total Length of Fwd Packet', 'Total Length of Bwd Packet', 'Fwd Packet Length Max', 'Fwd Packet Length Min', 'Bwd Packet Length Min', 'Bwd Packet Length Mean', 'Bwd Packet Length Std', 'Flow Bytes/s', 'Flow IAT Mean', 'Flow IAT Min', 'Fwd IAT Std', 'Fwd IAT Min', 'Bwd IAT Mean', 'Bwd IAT Std', 'Bwd IAT Max', 'Bwd IAT Min', 'Fwd PSH Flags', 'Fwd Header Length', 'Bwd Header Length', 'Bwd Packets/s', 'Packet Length Min', 'FIN Flag Count', 'SYN Flag Count', 'ACK Flag Count', 'Down/Up Ratio', 'Bwd Segment Size Avg', 'Bwd Bulk Rate Avg', 'Subflow Fwd Bytes', 'Subflow Bwd Bytes', 'FWD Init Win Bytes', 'Fwd Act Data Pkts', 'Fwd Seg Size Min', 'Idle Std', 'Idle Max', 'Idle Min']
features in the blue area: ['Flow Duration', 'Flow IAT Max', 'Fwd IAT Total', 'Fwd IAT Mean', 'Fwd IAT Max', 'Idle Mean'


|   |    CTU-13      |    CICIDS2017    |    NIDS Auto    |    NIDS Human    |
|---|----------------|------------------|-----------------|------------------|
| Src Port  | 0.01870   | 0.02925  | 0.00344  |   |
| Dst Port  | 0.03436  | 0.05697  | 0.05814  |   |
| Protocol  | 0.00082  | 0.01640  | 0.00001  |   |
| Timestamp  | 0.32922 | 0.07393  | 0.15306  |   |
| Flow Duration  | 0.01564  | 0.00183  | 0.01140  |   |
| Total Fwd Packet  | 0.00529  | 0.00402  | 0.00801  |   |
| Total Bwd packets  | 0.00472 | 0.00180  | 0.00048  |   |
| Total Length of Fwd Packet  | 0.00157 | 0.01671  | 0.04909  |   |
| Total Length of Bwd Packet  | 0.00178   | 0.00914  | 0.00044  |   |
| Fwd Packet Length Max  |  0.00573 | 0.00269  | 0.03238  |   |
| Fwd Packet Length Min  | 0.00079  | 0.00076  | 0.02321  |   |
| Fwd Packet Length Mean  | 0.00158  | 0.02320  | 0.00125  |   |
| Fwd Packet Length Std  | 0.00086 | 0.00155  | 0.00896  |   |
| Bwd Packet Length Max  | 0.00080  | 0.01416  | 0.01614  |   |
| Bwd Packet Length Min  | 0.00033  | 0.02625  | 0.00818  |   |
| Bwd Packet Length Mean  | 0.00394  | 0.08841  | 0.00510  |   |
| Bwd Packet Length Std  | 0.00044  | 0.01207  | 0.00024  |   |
| Flow Bytes/s  | 0.00682  | 0.00272  | 0.00076  |   |
| Flow Packets/s  | 0.00383  | 0.00213  | 0.01691  |   |
| Flow IAT Mean  | 0.00991   | 0.01294  | 0.00177  |   |
| Flow IAT Std   | 0.01147  | 0.00261  | 0.01333  |   |
| Flow IAT Max  | 0.00713  | 0.00330  | 0.02396  |   |
| Flow IAT Min  | 0.00731  | 0.00643  | 0.00343  |   |
| Fwd IAT Total  | 0.00904  | 0.00239  | 0.00047  |   |
| Fwd IAT Mean  | 0.03296   | 0.00842  | 0.00015  |   |
| Fwd IAT Std  | 0.00353  | 0.03824  | 0.00015  |   |
| Fwd IAT Max  | 0.01188 | 0.00953  | 0.00051  |   |
| Fwd IAT Min  | 0.01024  | 0.00854  | 0.00204  |   |
| Bwd IAT Total  | 0.00478  | 0.00173  | 0.00150  |   |
| Bwd IAT Mean  | 0.00232  | 0.00130  | 0.00770  |   |
| Bwd IAT Std  | 0.00186  | 0.00174  | 0.00453  |   |
| Bwd IAT Max  | 0.00323  | 0.00363  | 0.00003  |   |
| Bwd IAT Min  | 0.00187  | 0.00068  | 0.00606  |   |
| Fwd PSH Flags  | 0.00004   | 0.00143  | 0.00000  |   |
| Bwd PSH Flags  | 0.00000 | 0.00000  | 0.00000  |   |
| Fwd URG Flags  | 0.00000 | 0.00000  | 0.00000  |   |
| Bwd URG Flags  | 0.00000  | 0.00000  | 0.00000  |   |
| Fwd Header Length  | 0.04133  | 0.02192  | 0.00831  |   |
| Bwd Header Length  | 0.00899  | 0.01627  | 0.01644  |   |
| Fwd Packets/s   | 0.00487  | 0.00288  | 0.00069  |   |
| Bwd Packets/s   | 0.00336  | 0.01145  | 0.00053  |   |
| Packet Length Min  | 0.00104  | 0.00172  | 0.00013  |   |
| Packet Length Max  | 0.00735   | 0.04352  | 0.05280  |   |
| Packet Length Mean  | 0.00085  | 0.02144  | 0.00238  |   |
| Packet Length Std  | 0.00619 | 0.01480  | 0.03247  |   |
| Packet Length Variance  | 0.00553  | 0.01050  | 0.02247  |   |
| FIN Flag Count  | 0.00174   | 0.00125  | 0.00425  |   |
| SYN Flag Count  | 0.00602  | 0.00042  | 0.01898  |   |
| RST Flag Count  | 0.00150 | 0.00000  | 0.00068  |   |
| PSH Flag Count  | 0.00184  | 0.00279  | 0.00000  |   |
| ACK Flag Count  | 0.00684  | 0.00285  | 0.00833  |   |
| URG Flag Count  | 0.00000  | 0.00938  | 0.00000  |   |
| CWE Flag Count  | 0.00000  | 0.00000  | 0.00033  |   |
| ECE Flag Count  | 0.00000 | 0.00000  | 0.00017  |   |
| Down/Up Ratio   | 0.00215  | 0.00739  | 0.00559  |   |
| Average Packet Size  | 0.00426  | 0.08744  | 0.02772  |   |
| Fwd Segment Size Avg  | 0.00344  | 0.04174  | 0.02114  |   |
| Bwd Segment Size Avg  |  0.00513  | 0.07268  | 0.00098  |   |
| Fwd Bytes/Bulk Avg  | 0.00000  | 0.00000  | 0.00000  |   |
| Fwd Packet/Bulk Avg  | 0.00000 | 0.00000  | 0.00000  |   |
| Fwd Bulk Rate Avg  | 0.00000  | 0.00000  | 0.00000  |   |
| Bwd Bytes/Bulk Avg  | 0.00000  | 0.00000  | 0.00000  |   |
| Bwd Packet/Bulk Avg  | 0.00355  | 0.00000  | 0.00013  |   |
| Bwd Bulk Rate Avg   | 0.00034  | 0.00000  | 0.01019  |   |
| Subflow Fwd Packets  | 0.00022  | 0.00329  | 0.00000  |   |
| Subflow Fwd Bytes  | 0.00164  | 0.02293  | 0.00641  |   |
| Subflow Bwd Packets  | 0.00000  | 0.01634  | 0.00000  |   |
| Subflow Bwd Bytes  | 0.00264  | 0.04422  | 0.00839  |   |
| FWD Init Win Bytes  | 0.02668  | 0.00727  | 0.04705  |   |
| Bwd Init Win Bytes  | 0.00305   | 0.02130  | 0.04736  |   |
| Fwd Act Data Pkts  | 0.00202  | 0.00810  | 0.00669  |   |
| Fwd Seg Size Min  | 0.00699 | 0.00912  | 0.04107  |   |
| Active Mean  | 0.00000    | 0.00051  | 0.00000  |   |
| Active Std  | 0.00000   | 0.00036  | 0.00000  |   |
| Active Max  | 0.00000  | 0.00309  | 0.00000  |   |
| Active Min  | 0.00000  | 0.00025  | 0.00000  |   |
| Idle Mean  | 0.11999  | 0.00084  | 0.05847  |   |
| Idle Std  | 0.00056  | 0.00015  | 0.00000  |   |
| Idle Max  | 0.13085  | 0.00227  | 0.02355  |   |
| Idle Min  | 0.03429  | 0.00266  | 0.06347  |   |
