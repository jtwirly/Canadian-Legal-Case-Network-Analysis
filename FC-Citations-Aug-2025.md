# Network Analysis of Federal Court Citations from August 2025

This is a network analysis using a data set of citation annotations from 22 Federal Court decisions issued in August 2025. 

<img width="3212" height="3224" alt="fc_dashboard" src="https://github.com/user-attachments/assets/e0ed077f-bcfd-4e05-afe2-c2aa673323fe" />

**Most-cited statutes/regs** (using the actual `Statute`/`Regulation` labels in the schema: IRPA leads with 7 cites, Federal Courts Act and Rules close behind — makes sense given 13 of 22 cases are immigration matters running through the Federal Courts' own procedural rules.

**Judge caseload**: Duchesne sat on 4 of the 22 decisions, Manson on 3 — those two account for nearly a third of the month's output.

**Subject matter**: 13 immigration, 4 tax, and one each of IP, Indigenous governance, consular/passport, security clearance, and employment/labour. This is a fairly typical FC docket mix — immigration judicial review dominates the Court's caseload nationally.

**Bridge nodes (the most interesting one)**: *Vavilov* is unsurprisingly the top bridge point — but the second-highest is *Muma v Canada (Attorney General)* (2025 FC 1369), the security-clearance case. That's not obvious from raw citation counts (it only cites 2+ authorities a couple of times each), but structurally it's the decision doing the most work to connect the immigration-heavy cluster to the rest of the graph — likely because it pulls in general administrative-law reasonableness doctrine that's shared with, but not identical to, the immigration cases' citation patterns. *Kuznetcov* (2025 FC 1367) plays a similar bridging role.

Caveat: this is a 22-case sample from a single month, so the "most-cited" and "bridge" findings reflect this snapshot, not the Federal Court's caseload generally — *Vavilov* dominance would hold up at any scale, but judge caseload and subject-matter mix would look different over a full year.

## Citation Network

Here's a closer look at the citation network analysis:
<img width="2362" height="1850" alt="fc_citation_network (1)" src="https://github.com/user-attachments/assets/481bc5be-da0a-447e-9460-3e9b2ecc1af9" />

This is a directed graph in networkx where each citing decision points to the authorities it cites "in full" (using only full-citation mentions to define canonical case nodes, so as not to double-count short forms like "Telfer" against "Canada v Telfer, 2009 FCA 23"). Each edge carries the treatment the annotator assigned (followed/applied, neutral, disapproved, etc.).

**Key numbers**:
- 226 unique nodes (22 citing decisions + 210 distinct authorities), 251 full-citation edges
- Undirected graph has 10 connected components; the largest holds 162 nodes — most of these unrelated immigration/tax/administrative-law cases still converge on a shared core of doctrine
- 149 of 251 edges are "followed/applied," only 1 is "not followed/disapproved" — this corpus is almost entirely decisions applying settled law, not distinguishing it

**Most-cited authorities** (by in-degree):
| Cited | Count | Note |
|---|---|---|
| *Vavilov* (2019 SCC) | 9 | Sets the standard-of-review framework — cited in nearly half the decisions |
| *Mason v Canada* | 5 | Applies/refines Vavilov in immigration context |
| *Access Copyright* (SCC) | 4 | Reasons-review adequacy standard |
| IRPA, SC 2001, c 27 | 4 | The statute itself, not case law |
| Federal Courts Rules / IRP Regulations | 3 each | |

**In-degree centrality** confirms *Vavilov* dominates the network (0.040, roughly double the next node) — unsurprising, since it's the controlling Canadian precedent on judicial review standard-of-review across virtually all federal administrative law.

Structural note: none of the 22 citing decisions cite each other — they're independent judgments handed down in the same month, all drawing on a common pool of precedent rather than forming a citation chain among themselves.

## Dataset

The data set used in this project was created during the A2AJ Research Sprint using Label Studio. To learn more about A2AJ, visit https://a2aj.ca/
