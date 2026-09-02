# SCC 2019 Term — Network Analysis

Exploratory network analysis of the Supreme Court of Canada's 2019 term, built on a [Label Studio](https://labelstud.io/) annotation export of 67 SCC decisions. Uses NetworkX to surface citation authority, judicial co-occurrence, dissent patterns, and statutory frequency.

<img width="3236" height="3383" alt="scc_network_analysis (1)" src="https://github.com/user-attachments/assets/dd2d255d-1f08-4021-9750-2d9da1e42fc8" />

---

## Dataset

The source file is a Label Studio JSON export containing 67 annotated SCC judgments. Each record includes:

| Field | Description |
|---|---|
| `case_name`, `year`, `date` | Case identity |
| `Majority` / `Dissent` / `Concurrence` / `Dissent in part` | Opinion spans (character offsets into full text) |
| `Cases cited` | Raw citation strings, including treatment terms (`applied`, `distinguished`, `referred to`, etc.) |
| `Statutes and regulations cited` | Legislation referenced |
| `Authors cited` | Secondary literature |
| `Neutral citation`, `Keywords`, `Headnote`, `Coram`, `Date` | Metadata spans |

Annotations were produced by human reviewers and follow Canadian legal citation conventions.

---

## Analysis

### 1. Citation Network (`DiGraph`)
A directed graph where each node is a 2019 SCC case and edges represent internal citations (one case in the corpus citing another). Citation strings are parsed and normalized against the corpus to resolve references.

**Key findings:**
- *R. v. Mills* (sexual assault records) is the most-cited case internally (5 citations), anchoring a cluster of interrelated criminal law decisions
- *Canada (Minister of Citizenship and Immigration) v. Vavilov* appears despite being decided late in the term, signalling its immediate influence on administrative law
- 27 internal edges across 67 nodes — a sparse but structured graph, consistent with a single-term corpus

### 2. Judge Co-occurrence Network (`Graph`)
An undirected weighted graph where nodes are judges and edge weight reflects the number of cases they sat together. Useful for tracking panel composition, recusals, and coalition patterns across terms.

### 3. Decision Type Distribution
Of 67 decisions: **38 unanimous (57%)**, **21 with dissent (31%)**, **13 with concurrence (19%)**. Roughly 4 in 10 cases produced a minority opinion — a contentious term by SCC standards.

### 4. Statutory Frequency
The *Criminal Code* appears in 22 cases, the *Civil Code of Québec* in 11, and the *Canadian Charter of Rights and Freedoms* in 10, reflecting the term's heavy criminal docket.

---

## Possible Extensions

- **Multi-term analysis** — stack exports from multiple terms to track how citation authority accretes over time
- **Dissent coalitions** — weight the judge graph by dissents-together rather than mere co-occurrence, to surface ideological clustering
- **Charter section mapping** — extract `s. N` references from keyword spans to build a section-level citation graph
- **Treatment classification** — distinguish `applied` vs `distinguished` vs `referred to` edges in the citation network for a richer picture of how precedent is being used
- **Community detection** — run Louvain or label propagation on the citation graph to identify doctrinal clusters

---

## Notes

- Internal citations only — the network is bounded to cases within this 67-case corpus. Most `Cases cited` entries point to older precedent outside the dataset and are not graphed.
- Judge name parsing uses the `Judges` field in the raw case text; minor normalization is applied (surname extraction) but edge cases in French-language name formatting may affect completeness.
- Label Studio exports include both `annotations` and `predictions` fields; only human `annotations` are used here.

## License

Data sourced from the Supreme Court of Canada's public judgment repository. The data set used in this project was created during the A2AJ Research Sprint using Label Studio. To learn more about A2AJ, visit https://a2aj.ca/. 
