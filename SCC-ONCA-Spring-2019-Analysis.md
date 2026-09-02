# SCC 2019 and ONCA Spring 2019 Analysis

This project anayzes 2019 Supreme Court of Canada (SCC) cases with Spring 2019 Ontario Court of Appeal (ONCA) cases using network analysis. It analyzes 448 cases across both courts, focused on the question of how authority flows vertically through the hierarchy.

<img width="3543" height="4628" alt="scc_onca_crosscourt (1)" src="https://github.com/user-attachments/assets/ada179e0-1255-4b9e-9c91-d49778fb896e" />

## Findings

Multi-court citation network (top) — SCC cases sit in the top band, ONCA in the bottom. Same-court citations in amber/blue; the thick teal arrows cutting across the dashed midline are the 9 cross-court edges where ONCA picked up and applied an SCC case from the same 2019 term — meaning the lower court was already absorbing the new precedent within months of it being handed down.

SCC case authority (bottom-left of row 2) — Stacked by citation type: amber = cited by SCC peers in the same term, teal = cited by ONCA. R. v. Barton (sexual assault jury instructions) and R. v. Calnen (circumstantial evidence in murder) are the clear standouts — both already propagating down to ONCA that same year. The ✦ marks cases that had a dissent; notably Calnen was a 5-4 split, yet ONCA applied it immediately and repeatedly.

SCC judge co-occurrence (top-right of row 2) — The 9-justice court is nearly complete, but edge weight reveals that Wagner, Moldaver, and Karakatsanis sat together on nearly everything. Côté and Brown co-occur slightly less — consistent with their more frequent dissents.

ONCA caseload + dissents (bottom-left) — The criminal/civil split and the dissent trend in purple. Dissents peak in May (4 cases) — a small but notable signal worth tracking across more terms.

Influence scatter (bottom-right) — The most analytically interesting panel: x-axis is how much a SCC case was cited internally (by SCC peers), y-axis is how much it crossed down to ONCA. Barton has the highest cross-court pull (2 ONCA citations) despite also having the most internal citations. Calnen drew the most ONCA citations (4) with modest internal SCC traffic — suggesting it resolved something the lower courts were particularly hungry for, fast.

The dominant finding: cross-court propagation in 2019 was almost entirely criminal law (Calnen, Barton, Bird, Jarvis, Mills). Civil and administrative law SCC decisions from the same term — including Vavilov — don't show up in ONCA yet, likely because the lag between grant and integration is longer for civil precedent. 

Future research could include testing against a full year ONCA dataset.

The data set used in this project was created during the A2AJ Research Sprint using Label Studio. To learn more about A2AJ, visit https://a2aj.ca/
