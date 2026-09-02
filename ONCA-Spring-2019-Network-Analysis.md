# ONCA Spring 2019 Network Analysis

This project uses NetworkX to analyze a database of 2019 Ontario Court of Appeal cases (ONCA) that are labeled by section. This is all the ONCA cases from March to June 2019.

<img width="3468" height="3682" alt="onca_network_analysis" src="https://github.com/user-attachments/assets/d626941a-3906-4913-8efc-d2feb15009da" />

# Observations

Five panels across 381 ONCA decisions from March–June 2019

Judge co-occurrence network (top): All 27 active judges who sat in ≥5 cases. Edge weight = how often any two sat together; colour = dominant subject area. Doherty, Benotto, Feldman, and Brown form the heavy core. Criminal-dominant judges (pink) tend to cluster slightly away from the civil bench (blue), though most ONCA judges straddle both.

Caseload by month and subject: Volume is relatively steady (~90–100 cases/month), but the criminal/civil split shifts. Civil edged criminal in April and May; criminal picked up in June. Family law is a small but consistent fraction (10–11 cases) throughout.

Courts cited: ONCA is most self-referential (526 internal citations), followed by SCC at 386 — roughly the expected hierarchy. ONSC (117) is notable; trial courts are cited far more often than other provincial appellate courts, consistent with how interlocutory and summary judgment appeals work in Ontario.

Activity heatmap: Doherty, Benotto, and Feldman are the most consistently active across all four months. Some judges spike in particular months (Hourigan in March, Fairburn in May), possibly reflecting sitting rotations or specialty panels.

Criminal vs civil split per judge: Watt and Paciocco are nearly entirely criminal (both former criminal law academics). Feldman, Lauwers, and Hourigan lean heavily civil. Most judges are more mixed than you'd expect — only a handful sit exclusively in one stream.

The data set used in this project was created during the A2AJ Research Sprint using Label Studio. To learn more about A2AJ, visit https://a2aj.ca/
