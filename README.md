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
- For more information on obtaining an API key, see: [API Key Documentation](https://docs.google.com/document/d/1Js1Xj_NuuYC8x61zmEqURXLiyvDdytJYSfC8IAgBW6Q/edit?pli=1&tab=t.0)

(You may omit any variables you do not need for your workshop session.)

**Note:** `.env` is excluded from version control for your security.

---

## Connecting to Neo4j AuraDB

For this workshop, you will need a Neo4j AuraDB instance. 

**Primary Method: Neo4j AuraDB ProTrial**

1. Go to [console.neo4j.io](https://console.neo4j.io/).
2. Sign up or log in to your Neo4j Aura account.
3. Create a new **Free Tier** or **ProTrial** instance. A ProTrial instance is recommended if available, as it provides more resources. Ensure GDS (Graph Data Science) is enabled or can be enabled on your instance.
4. Once your instance is running, note down your connection URI, username, and password. You will need these for your `.env` file.

**Alternative: Using the Provided Database Dump (Optional)**

If you prefer to run a local Neo4j instance or need to restore the database to a specific state, a dump file is available. This can also be loaded into an AuraDB instance if needed.

- **Download Link:** [Neo4j Dump File](https://drive.google.com/file/d/1e6E1E5trJObKK_yc6oFCCaiUcFSVmX1O/view?usp=sharing)

**Instructions for loading the dump (example using `neo4j-admin load` for local instances):**

1. Download the `.dump` file from the link above.
2. Stop your local Neo4j instance.
3. Run the load command (replace `your-database-name` and path to your dump file):
   ```sh
   neo4j-admin load --from=/path/to/your/downloaded.dump --database=your-database-name --force
   ```
4. Start your Neo4j instance.

If you are using an AuraDB instance created as per the primary method, connection details (URI, username, password) will be available directly from the Aura console. Your instructor may also provide details for a shared instance.

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

**Active Notebooks:**

- `01_Get_To_Know_Your_Graph.ipynb` – Graph and data exploration basics
- `02_Communities_and_KNN.ipynb` – Community detection, KNN, and graph analytics
- `Advanced_GraphRAG_Workshop_Final.ipynb` – Advanced Graph RAG and analytical workflows

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
