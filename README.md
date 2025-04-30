# graphai-insights: Behavioral Clustering, Influence Detection, Churn Prediction, Customer Experience

## Overview

This work is intended to transform raw telecom interaction data (MIT Dataset) into a **knowledge rich graph**, enabling  insights using **graph algorithms**, **embeddings**, and **LLMs (GraphRAG)**.

**Goal:**
- Given data on people, devices, phones, call records, and cell tower logs:
  - Identify influential individuals
  - Predict churn propensity using call activity and network centrality
  - Explore behavioral clusters to understand engagement & buying intent
  - Extract location-based signals through cell tower usage
  - Enable GraphRAG: interactive LLM-powered querying over graph insights

---
## About Dataset
The Reality Mining project was conducted from 2004-2005 at the MIT Media Laboratory. The Reality Mining study followed ninety-four subjects using mobile phones pre-installed with several pieces of software that recorded and sent the researcher data about call logs, Bluetooth devices in proximity of approximately five meters, cell tower IDs, application usage, and phone status. Subjects were observed using these measurements over the course of nine months and included students and faculty from two programs within a major research institution. We also collected self-report relational data from each individual, where subjects were asked about their proximity to, and friendship with, others
[Link to the dataset](http://realitycommons.media.mit.edu/realitymining.html)

## Data Sources
- `person`, `device`, `phonenumber`, `celltower` tables
- Call records and activity spans (e.g., person-device-tower interactions)
---

## Techniques

| Task | Technique |
|------|-----------|
| Graph Creation | NetworkX Graph from relational data |
| Community Detection | Louvain, HDBSCAN |
| Influence Estimation | Degree Centrality |
| Behavioral Embeddings | Node2Vec |
| Clustering | HDBSCAN on embeddings |
| Churn Detection | Drop-off in call activity + low centrality |
| Visualization | PCA + Matplotlib |
| LLM Integration | LangChain + OpenAI for GraphRAG |

---

## Key Outcomes

### Community & Influence Analysis
- Identified **influential individuals** (based on degree + cluster)
- Found **engagement clusters** via HDBSCAN and Node2Vec embeddings
- Example clusters:
  - Cluster 2: 937 devices, 570 towers
  - Cluster 3: 1035 devices, 1324 towers

### Churn Propensity
- People with **call activity drop-off** and low centrality marked as churn risks

### Location based Insights
- Aggregated tower usage per cluster and per person
- Derived mobility and behavioral patterns tied to geography

### Q&A - GraphRAG
- Interactive question-answering over the graph using LangChain + OpenAI
- Answered queries like:
  - "Who are the top influencers in cluster X?"
  - "Which person is likely to churn next month?"

---

## Saved Artifacts
- `graph.pkl` – Full interaction graph (Will upload later)
- `subgraph.pkl` – Pruned graph (degree-based subgraph)
- `node2vec.pkl` – Embedding model

---

## Planned Enhancements
- Add real-time GraphDB integration (Targeting Neo4j)
- Exploring other relevant algorithms for the outcomes planned (time-series, Clustering, Neural Network)
- Enhance GraphRAG techniques for better response

---

## Credits

@2025 Vinoth Sukumaran - used Python, NetworkX, Louvain, Node2Vec, HDBSCAN, and OpenAI's LLMs.

Dataset used - [Link to the dataset](http://realitycommons.media.mit.edu/realitymining.html)

