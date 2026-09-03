# Court Metrics

This data set contains 184,565 decisions across 14 courts from 1877 to mid-2026, with per-decision metrics. Claude and NetworkX were used to analyze it.

## Court Similarity Graph

<img width="3334" height="4638" alt="court_metrics_analysis (1)" src="https://github.com/user-attachments/assets/84b4a15f-b25f-471d-a741-8b2cf2ccb729" />

The network here is a **court similarity graph** built from cosine similarity of each court's metric profile (word count, FK grade, citation count). 

Five panels:

**Similarity network (top)** — Courts cluster into two loose groups: the tribunal tier (RAD, SST, RPD, RLLR) and the generalist courts (FC, FCA, ONCA, BCCA, TCC). SCC sits alone — its metric profile is genuinely distinct from every other court. The node sizes make the length gap obvious: SCC decisions average ~12,300 words while ONCA averages ~2,600. Edges are only drawn above a 0.985 cosine similarity threshold, so visible connections are real metric resemblances.

**Word count trends (mid-left)** — The SCC's length explosion is striking: median decisions were ~8,000 words in the early 2000s and are now pushing 23,000 in 2024. BCCA also grew sharply, doubling since 2015. FC, FCA, and ONCA have been more stable. The 2020 COVID bump is visible across multiple courts — likely pandemic-era backlog decisions running longer.

**FK readability (mid-right)** — FC and the tribunal courts (SST, RAD) consistently score the hardest to read (FK 12–14), driven by immigration and administrative law's technical vocabulary. ONCA and BCCA sit around 10–11 — roughly post-secondary reading level. Notably, FK grades are fairly flat over time: courts aren't getting meaningfully more or less readable, they're just getting longer.

**Citation count distribution (bottom-left)** — SCC's IQR is far right of every other court, median around 28 citations per decision. CHRT and CMAC have surprisingly high medians for their size. RPD and RLLR have the lowest — refugee and labour decisions tend to resolve on facts rather than extensive case law.

**Complexity scatter (bottom-right)** — The cleanest panel. SCC is an outlier in the top-right (long and moderately readable). FC is the other anomaly: it's roughly average length but has the highest FK grade of any court — immigration judicial review produces technically dense but not especially long decisions. Tribunals cluster bottom-left: short and hard to read.

## Individual Charts

**A court trend-similarity graph**

<img width="2141" height="1603" alt="court_network" src="https://github.com/user-attachments/assets/edd6ad20-8519-4850-b72c-2ec7e7f7c868" />
<img width="1961" height="1061" alt="court_centrality" src="https://github.com/user-attachments/assets/f0bdfea7-caaa-4741-9267-14cedce8f0e8" />

How it's built:
1. Aggregated case counts per court per year (2000–2025)
2. Z-scored each court's yearly volume so I'm comparing the shape of the trend, not raw size
3. Computed pairwise Pearson correlation between every pair of courts
4. Drew an edge when |correlation| ≥ 0.5 — green solid = courts that rise/fall together, red dashed = courts that move oppositely

Analysis:
-SST (Social Security Tribunal) is the most central court by degree, eigenvector, and betweenness centrality — its caseload trend is entangled with the most other courts
-Two natural clusters emerge: a federal-tribunal cluster (FC, FCA, TCC, RPD, SCC) and an appeals/SST cluster (ONCA, RAD, RLLR, SST, YKCA)
-BCSC and CMAC are isolates — their yearly volume trends don't correlate strongly (≥0.5) with any other court, despite BCSC having the largest raw case count in the dataset

**Word count trends** — median decision length per court per year, direct end-of-line labels stacked without collision. SCC stands out with a sharp length increase since 2020.
<img width="2321" height="1329" alt="word_count_trends" src="https://github.com/user-attachments/assets/948e2f5c-37d9-41f4-b016-a4622b13446b" />

**FK readability** — horizontal boxplots sorted by median grade level; FC and RLLR/RAD tribunal decisions read as most complex, BCSC/BCCA/YKCA as most readable.
<img width="1962" height="1421" alt="fk_readability" src="https://github.com/user-attachments/assets/e8fd080a-012f-4d1b-a8d5-60426e7c9c88" />

**Citation count distribution** — log-scale histogram (most decisions cited 0-10 times, long tail to 322) plus median-vs-mean by court, showing SCC has by far the highest mean (~30) despite modest median, driven by a few heavily-cited landmark cases.
<img width="2499" height="1057" alt="citation_distribution" src="https://github.com/user-attachments/assets/4d85ca57-18f0-4fa4-b406-52a24a346957" />

**Complexity scatter** — hexbin density of word count vs. FK grade across all 173k decisions, with the 8 most-cited outlier cases individually labeled (including the *Cambie Surgeries* case, a 300k+ word outlier).
<img width="1994" height="1421" alt="complexity_scatter" src="https://github.com/user-attachments/assets/678773d0-3a03-479c-8491-1a3e9fb83531" />

**Temporal network** — the trend-similarity network split into three eras, showing the correlation structure has gotten *denser* over time (15 → 32 → 22 edges) as more tribunals (RAD, RLLR, SST) came online and synchronized.
<img width="3383" height="1234" alt="temporal_network" src="https://github.com/user-attachments/assets/6581e725-618a-411e-a156-2e7ecfdfd7bf" />

**Metrics similarity network** — a different network built on cosine similarity of writing-style profiles (word/sentence count, FK grade, citations) rather than time-trend correlation — shows FC, SST, RAD, RLLR cluster together (tribunal-style writing) distinct from BCSC/BCCA/SCC (court-style).
<img width="2141" height="1603" alt="metrics_similarity_network" src="https://github.com/user-attachments/assets/b65e42ac-f2cf-41bb-849f-b32a1c0853f8" />

