# Analysis of Trenitalia’s Railway Network

**Authors:** Francesco Vece, Riccardo Spini  
**Course:** Social Network Analysis  
**Date:** June 2024  

---

## Overview

This project analyzes the structure and properties of the **Italian railway network** operated by **Trenitalia**, focusing on its **connectivity**, **robustness**, and **community structure** using tools from **graph theory** and **network analysis**.

The goal is to provide insights into how well-connected the network is, which cities are most central, and how the system behaves under simulated failures.

---

## Problem & Motivation

- Identify critical hubs and assess connectivity between cities.
- Understand the network's resilience and vulnerabilities.
- Support future planning and sustainable expansion of the rail system.

---

## Dataset

### Data Collection

Train routes were collected from the [Trenitalia public API](https://github.com/TrinTragula/api-trenitalia) and validated against the official weekly schedule (27/05/2024 – 02/06/2024).

### Geolocation Data

City coordinates were retrieved from [Garda Informatica](https://www.gardainformatica.it/) to enable geographical visualization.

### Files Used

- `treni_solo_città.csv`: Train trips reduced to origin and destination cities.
- `merged_data.csv`: Geolocation data (latitude, longitude) for Italian municipalities.

---

## Tools & Technologies

- **Python**  
- `pandas` – Data manipulation  
- `networkx` – Graph creation and centrality metrics  
- `matplotlib` – Static visualization  
- `folium` – Interactive geographic visualization  

---

## Methodology

### Network Construction

- The network is modeled as an **undirected, unweighted monopartite graph**.
- **Nodes**: Italian cities  
- **Edges**: Direct connections by Trenitalia trains

### Preprocessing

- Grouped multiple stations (e.g., Roma Termini, Tiburtina) into one city node.
- Simplified representation for a national-level view.

---

## Measures & Results

### Centrality

- **Degree Centrality**: Identifies highly connected cities (e.g., Milan, Rome).  
- **Betweenness Centrality**: Detects key transfer hubs.  
- **Eigenvector Centrality**: Highlights cities central in strategic connections.

### Other Metrics

| Metric                         | Result                     |
|-------------------------------|----------------------------|
| Network Density               | 0.0108                     |
| Connected Components          | 1 (fully connected)        |
| Degree Assortativity          | -0.1383 (disassortative)   |
| Number of Bridges             | 140                        |
| Modularity (Community Score) | 0.654                      |

---

## Simulations

We evaluated the network's robustness through two simulations:

1. **Random City Removal (5 nodes)**  
   → Minor impact on connectivity.

2. **Worst-Case Removal (Top 5 by Degree Centrality)**  
   → Severe fragmentation into 49 components.

| Scenario         | Density       | Components |
|------------------|---------------|------------|
| Default          | 0.01084       | 1          |
| Random Removal   | 0.00951       | ~1.16      |
| Worst Case       | 0.00785       | 49         |

---

## Visualizations

- Cities plotted on Italy’s map using `folium`.
- Central cities highlighted in **red**.
- Community structures visualized to show regional clustering.

---

## Conclusions

- The Trenitalia network behaves like a **scale-free** network, centered around few key hubs.
- It is **robust to random failures** but **fragile to targeted attacks** on major cities.
- Community detection shows **regional clustering**, confirming strong intra-regional connectivity.

---

## Critique & Future Work

- Intermediate stops were excluded: current analysis only considers **origin-destination pairs**.
- Future improvements:
  - Include full train itineraries.
  - Automate data extraction via AI tools.
  - Use temporal graphs for dynamic analysis.

---

## Repository

🔗 [GitHub Project](https://github.com/riccardospini98/sna)

---

> This project was developed for educational purposes as part of the *Social Network Analysis* course.
