# BCCA Spring 2019 and SCC 2019 Cases

A network analysis of BCCA Spring 2019 cases and SCC 2019 cases.

This project uses a labeled data set with cases of BC Court of Appeal (145 cases, Jan–Apr 2019) and Supreme Court of Canada (67 cases, 2019) judgments.

## Findings

**Judge co-panel networks (figs 1–2)** — nodes = judges, edge weight = # times sat together, node color = dissent rate. Willcock, Fisher, and Fitch were BCCA's most active panelists this period; the court is a fairly dense, single connected clique (25 judges, 130 co-sitting pairs), with Fenlon and Newbury scoring highest on betweenness centrality — they're the judges who most often bridge otherwise-separate panel groupings. On the SCC side, Kasirer (newly appointed) is a peripheral node with only 5 sittings, while Côté, Brown, Abella, Karakatsanis, and Rowe show the highest dissent rates.
<img width="1800" height="1500" alt="fig1_bcca_panel_network" src="https://github.com/user-attachments/assets/09b63188-865d-4d94-8e68-da0b25f4c318" />
<img width="1650" height="1350" alt="fig2_scc_panel_network" src="https://github.com/user-attachments/assets/d6c4cb93-3d5c-4721-b5da-5ae31f271d37" />

**"SCC Dissented-from" network (fig 3)** — directed edges from dissenting judge → majority author. Côté is the most frequent dissenter overall and dissents from nearly every colleague; Rowe and Brown also dissent broadly, while Wagner (Chief Justice) and Moldaver anchor the majority far more often than they dissent.
<img width="1650" height="1350" alt="fig3_scc_dissent_network" src="https://github.com/user-attachments/assets/c25d5751-7a25-47d4-801c-271741bc6e11" />

**Citation network (fig 4)** — parsed the "Cases cited" field across all 67 SCC judgments (2,596 citation entries) into a directed citation graph. *Rizzo & Rizzo Shoes Ltd. (Re)* (statutory interpretation) and *Housen v. Nikolaisen* (standard of review) are the most-relied-on precedents.
<img width="1500" height="1200" alt="fig4_most_cited_precedents" src="https://github.com/user-attachments/assets/ab6314d2-71f3-454d-ba06-542b64f9f160" />

**Cross-reference (fig 5)** — searched all SCC citations for "BCCA" mentions: 29 citations across 18 different SCC 2019 judgments cite BC Court of Appeal precedents (e.g., *R. v. Colley*, *R. v. Cadman*). None of these happen to overlap with the specific 145 cases in your Jan–Apr BCCA file (SCC citations of BCCA typically lag by years), but it does show BCCA's ongoing influence at the SCC level, especially in criminal law.
<img width="1950" height="1207" alt="fig5_scc_cites_bcca" src="https://github.com/user-attachments/assets/60564868-5bea-4a89-90ff-3f520411b50a" />

**Origin courts (fig 6)** — most BCCA appeals (116/145) came from BC Supreme Court orders, versus 18 from Provincial Court.
<img width="1350" height="750" alt="fig6_bcca_origin_courts" src="https://github.com/user-attachments/assets/67599dc9-bbd9-4c37-84ad-47c88af06732" />

Data-quality note: A couple of inconsistent judge-name variants (e.g. "MacKenzie" vs "A.W. MacKenzie") were merged, and one mislabeled annotation was dropped ("Appellants" tagged as a Panel entry). 

This project could be extended by building a full name-resolved citation graph between the two courts, or adding more SCC years to check for direct BCCA→SCC appeal chains.
