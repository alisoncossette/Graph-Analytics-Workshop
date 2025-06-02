# Graph Analytics Workshop

Welcome to the **Graph Analytics Workshop**! This repository contains all materials, code, and instructions for hands-on exploration of advanced graph analytics, Retrieval Augmented Generation (RAG), and knowledge graphs using Neo4j and Python.

---

## Workshop Overview

- **Title:** Graph Intelligence: Enhance Reasoning and Retrieval Using Graph Analytics
- **Level:** Advanced
- **Duration:** 2 hours
- **Format:** Hands-on, notebook-driven technical deep dive
- **Slide Deck:** [Beyond Vectors (Google Slides)](https://docs.google.com/presentation/d/1qSpw2KzSEgALbb59Gn5yZBIfSUinWtbFzMzcs6ur_8k/edit?usp=sharing)

### What You'll Learn
- How to use graph analytics and ML for reasoning and retrieval
- Working with Neo4j knowledge graphs and vector search
- Advanced GraphRAG techniques for GenAI applications
- Practical data exploration, quality checks, and visualization

---

## Prerequisites

- Basic familiarity with Python and Jupyter Notebooks
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (optional, if running locally)
- A Neo4j AuraDB instance (connection details provided by the instructor/company)
- Python 3.9+

---

## Environment Setup

### 1. Clone the Repository
```sh
git clone <this-repo-url>
cd Graph-Analytics-Workshop
```

### 2. Python Virtual Environment
```sh
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```sh
pip install -r requirements.txt
```

### 4. Set Up Your `.env` File
Create a `.env` file in the project root with the following variables:
```env
NEO4J_URI=neo4j+s://<your-instance>.databases.neo4j.io
NEO4J_USERNAME=<your-username>
NEO4J_PASSWORD=<your-password>
OPENAI_API_KEY=<your-openai-key>
```
(You may omit any variables you do not need for your workshop session.)

**Note:** `.env` is excluded from version control for your security.

---

## Connecting to Neo4j AuraDB

The workshop uses a prepopulated Neo4j AuraDB instance. Connection details will be provided by your instructor or company admin.

Test your connection by running the following code in a notebook cell:
```python
from neo4j import GraphDatabase
import os
from dotenv import load_dotenv

load_dotenv()
uri = os.getenv("NEO4J_URI")
user = os.getenv("NEO4J_USERNAME")
pw = os.getenv("NEO4J_PASSWORD")
driver = GraphDatabase.driver(uri, auth=(user, pw))
with driver.session() as session:
    result = session.run("MATCH (n) RETURN count(n) AS node_count")
    print("Node count:", result.single()["node_count"])
```

---

## Running the Notebooks

1. Activate your virtual environment.
2. Start Jupyter:
   ```sh
   jupyter notebook
   ```
3. Open the notebooks in the `notebooks/` directory and follow along with the workshop exercises.

---

## Workshop Structure

- **01_intro_to_rag_and_graphs.ipynb** – RAG overview, why graphs, simple pipeline
- **02_neo4j_graph_basics.ipynb** – Neo4j nodes, relationships, properties, connection
- **03_data_sources_and_quality.ipynb** – EDA, data quality, visualization
- **04_graph_analytics_and_algorithms.ipynb** – Graph projection, analytics, visualization
- **05_advanced_graphrag.ipynb** – Integrating Neo4j with LLMs, hybrid retrieval

---

## Troubleshooting & Support

- **Neo4j Connection Issues:**
  - Double-check your `.env` variables and credentials
  - Ensure your AuraDB instance is running and accessible
- **Python/Package Issues:**
  - Ensure your virtual environment is activated
  - Run `pip install -r requirements.txt` again if needed
- **General Help:**
  - Ask your instructor or workshop helpers for support

---

## Credits & References
- Workshop slide deck: [Beyond Vectors](https://docs.google.com/presentation/d/1qSpw2KzSEgALbb59Gn5yZBIfSUinWtbFzMzcs6ur_8k/edit?usp=sharing)
- Reference code: [NODES2023_GenAI_GDS_Analysis.ipynb](https://github.com/danb-neo4j/NODES2023_GDS_GenAI/blob/main/NODES2023_GenAI_GDS_Analysis.ipynb)
- Powered by Neo4j AuraDB, Graph Data Science, and Python

---

Enjoy the workshop and happy graph exploring!
