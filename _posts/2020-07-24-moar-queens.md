---
layout: post
title: "moar queens"
date: 2020-07-24
---
## Reprocessing
We decided to add back the `Timestamp`, `Protocol`, and `Flow Bytes/s` / `Flow Packets/s` (without all the inf and NaNs). Thus, we had to reprocess the old flows into new queens.

Complete! [Reprocessing CICIDS](/assets/CICIDS-reprocess-072620.html)

Complete! [Reprocessing NIDS-Auto](/assets/NIDS-AML-Auto-reprocess-072620.html)

Complete! [Reprocessing CTU-13](/assets/CTU-13-reprocess-072620.html)

Complete! [Reprocessing NIDS-Human](/assets/NIDS-AML-Human-reprocess-072620.html)



## Boruta
Complete! [Boruta CTU-13 072620](/assets/Boruta-CTU-13-072620.html)

Complete! [Boruta CICIDS 072620](/assets/Boruta-CICIDS-072620.html)

Complete! [Boruta NIDS AML Auto 072120](/assets/Boruta-NIDS-AML-Auto-072120.html)

Complete! [Boruta NIDS AML Human 072920](/assets/Boruta-NIDS-AML-Human-072920.html)

## Visualizing Progress
I had graphed this in Excel, but we can do better:

<img src="/assets/sns-boruta.png" width="800">

<img src="/assets/sns-no-boruta.png" width="800">

You can find the whole caboodle here:

[Heatmap Notebook](/assets/Results-Heatmap.html)

## Normalizing Across
Using scikit learn's Normalize method with the `max`, `l1`, and `l2` modifiers
and graphing the results.

[Heatmap Notebook](/assets/Results-Heatmap-082420.html)
