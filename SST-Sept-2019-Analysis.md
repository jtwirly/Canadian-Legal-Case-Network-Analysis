# Social Security Tribunal September 2019 Network Analysis

This is an analysis Canadian Social Security Tribunal decisions, with 154 case files of Employment Insurance decisions from September 2019 in the data set, each annotated with metadata (member, division, citation) and full decision text.  

**1. Case citation network** (399 nodes, 460 edges)
Looks at which precedent cases each decision cites.
<img width="2685" height="1327" alt="sst_citation_network" src="https://github.com/user-attachments/assets/abb5e67d-f3c2-44c4-8976-bbb05c760b41" />
- Directed graph: each SST decision → each precedent case (FCA/FC/SCC) it cites, extracted via regex from the decision text
- 41 weakly-connected components; the largest holds 70% of all nodes — most decisions draw from one shared body of EI jurisprudence
- Top hub precedent: **2001 FCA 248**, cited by 20 of the 154 decisions — the most load-bearing precedent in this corpus
- Found 5 rare **internal cross-citations**, where one 2019 SST decision cites another decision from the same batch — including a genuinely reciprocal pair (2019 SST 1256 ↔ 1253) and a General Division ↔ Appeal Division pair on the same underlying case

**2. Member similarity network** (48 adjudicators, 274 edges)
A **member/precedent bipartite network** to see shared jurisprudence (which adjudicators cite overlapping precedents / decide similar case types).
<img width="1935" height="1632" alt="sst_member_network" src="https://github.com/user-attachments/assets/d2c82f56-6360-41fe-baac-b37a1f2cf8cc" />
- Bipartite projection: two members are linked if they cited overlapping precedents, weighted by how many precedents they share
- Ran greedy modularity community detection → found 3 real clusters (sizes 22, 18, 5) plus a few isolates
- Interesting finding: weighted-degree centrality doesn't track case volume — e.g. Brisette Lucas and Anne Clark each decided only 1 case in this window but are highly central because their single case cited many widely-shared precedents, while high-volume members like Stephen Bergen (15 cases) sit in their own smaller cluster (community 3) with more idiosyncratic citation patterns
