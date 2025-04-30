# graphai-insights: Behavioral Clustering, Influence Detection, Churn Prediction, Customer Experience

## Overview

This work is intended to transform raw telecom interaction data (MIT Dataset) into a **knowledge rich graph**, enabling  insights using **graph algorithms**, **embeddings**, and **LLMs (GraphRAG)**.

**Goals**
- Ingest and model person-device-tower-phone interactions as a graph
- Identify influential individuals via network centrality
- Detect churn risks based on temporal and structural patterns
- Discover behavioral clusters using unsupervised techniques
- Derive mobility and social signals through tower usage and call patterns
- Enable LLM-driven querying over graph data (GraphRAG)

---
## About Dataset
The Reality Mining project was conducted from 2004–2005 at the MIT Media Lab. It tracked 94 individuals via mobile devices pre-installed with software that captured:
- Call logs
- Bluetooth proximity (approx. 5 meters)
- Cell tower IDs
- Application usage
- Phone status

Subjects were from two academic programs and observed for nine months.

[Link to the dataset](http://realitycommons.media.mit.edu/realitymining.html)

## Data Sources
- Relational tables: `person`, `device`, `phonenumber`, `celltower`
- Interactions: Call logs, proximity detections, location-based movements

---

## Techniques

| Task | Technique |
|------|-----------|
| Graph Creation | Build multi-node interaction graph with NetworkX |
| Embeddings | Node2Vec |
| Community Detection | Louvain, Agglomerative Clustering |
| Influence Estimation | Degree Centrality |
| Visualization | PCA + Matplotlib + Plotly |
| Clustering | Agglomerative Clustering on embeddings |
| Churn Detection | Drop-off in call activity + low centrality |
| Location Patterns | Analyze tower usage per person & per cluster |
| LLM Integration | LangChain + OpenAI for GraphRAG |

---

## Key Functionalities

### Graph Creation
- Nodes: Person, Device, Phone, Tower
- Edges: Calls, proximity events, device-tower mappings
- Network built using NetworkX

### Embedding & Clustering
- Node2Vec → behavior embeddings
- Louvain → community detection
- PCA → 2D visualization of clusters

### Influence Analysis
- Degree centrality used to rank influential individuals
- Subgraph pruning for top influencers

### Community & Influence Analysis
- Identified **influential individuals** (based on degree + cluster)
- Found **engagement clusters** via Agglomerative Clustering and Node2Vec embeddings
- Example clusters:
  - Cluster 2: 937 devices, 570 towers
  - Cluster 3: 1035 devices, 1324 towers
    
### Churn Prediction
- Drop in monthly call volume + low degree centrality
- Output: List of churn-likely users

### Location Insights
- Aggregate tower interactions by person and cluster
- Extract mobility behavior and geographic footprint

### GraphRAG: LLM Q&A
- Use LangChain + OpenAI to answer questions on:
  - Top influencers
  - Likely churners
  - Cluster characteristics
- Graph context embedded for LLM responses

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

