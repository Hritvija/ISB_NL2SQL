# NL2SQL Dashboard — Fine-tuned GGUF Model  

### Generative AI Internship — Indian School of Business, Hyderabad (Jan 2025 – Aug 2025)  
**Author:** Hritvija Singh  
📧 [hritvijasi22@iitk.ac.in](mailto:hritvijasi22@iitk.ac.in)  

---

## Overview  

This project was developed as part of the **Generative AI Internship** at the **Indian School of Business (ISB), Hyderabad**.  
It demonstrates a **Natural Language to SQL (NL2SQL)** system powered by a **fine-tuned CodeLLaMA-7B model (GGUF format)** that translates plain English questions into executable **SQLite SQL queries** — and visualizes real-time results.

The model and dashboard enable **non-technical users** to interact with structured databases through natural language, streamlining data exploration and analytics workflows.

---

## Features  

✅ Fine-tuned **CodeLLaMA-7B (QLoRA)** model achieving **92% query match accuracy**  
✅ Converts natural language to SQL queries instantly  
✅ Visualizes tabular results directly from the database  
✅ Handles **complex relational schema** across Subordinate ↔ FM ↔ RM hierarchies  
✅ Runs entirely **locally** using `llama-cpp-python`  

---

## Project Architecture  

**Pipeline:**  
```
User Query → LLM (CodeLLaMA GGUF) → SQL Query → SQLite Database → Visualization (Streamlit)
```

---

## Repository Structure  

```
ISB_NL2SQL/
├── ISB_frontend/           # Streamlit dashboard UI
├── backend/                # FastAPI backend for LLM inference
├── app.py                  # Streamlit app entrypoint
├── dash.py                 # Dashboard logic and SQL rendering
├── start.sh                # Launch script
├── requirements.txt        # Python dependencies
├── survey_isb.db           # SQLite database
└── README.md               # (this file)
```

---

## Technical Approach  

### Data & Schema  
- Designed a **role-aware relational schema** connecting Subordinate ↔ FM ↔ RM for 500+ survey responses.  
- Built an **ETL pipeline (Python + Qualtrics API)** to normalize CSVs into relational tables within 90 seconds.

### Model Training  
- Fine-tuned **CodeLLaMA-7B** using **QLoRA** on **9.3k NL→SQL pairs**.  
- Quantized model to **GGUF** format for CPU-friendly deployment via `llama-cpp-python`.  

### Application Layer  
- Implemented **Streamlit dashboard** for user queries and live SQL visualization.  
- Backend built with **FastAPI** to handle inference requests.  

---

## How to Run Locally  

### Clone the Repository  
```bash
git clone https://github.com/Hritvija/ISB_NL2SQL.git
cd ISB_NL2SQL
```

### Install Dependencies  
```bash
pip install -r requirements.txt
```

### Run the Application  
```bash
bash start.sh (check the path)
# or
streamlit run app.py
```

### Query Example  
Input:  
```
list name and email of users above age 30
```

Generated SQL:  
```sql
SELECT name, email FROM Users WHERE age > 30;
```

---

## Dashboard Preview  

Below is a working preview of the NL2SQL dashboard — showcasing query input, SQL generation, and real-time database output visualization.

![DEMO_ISB](https://github.com/user-attachments/assets/42bf99f3-6fbc-40e8-8712-de35e0edd1b7)


---

## Deployment Note  

Full deployment was **not possible** on free hosting platforms (e.g., Render, Hugging Face Spaces) because they **do not support LLM execution or GGUF quantized inference**.  
However, the app runs **smoothly on local systems**, with fast response times (~1.8 s per query) using `llama-cpp-python`.

---

## Tech Stack  

| Layer | Technologies |
|:------|:--------------|
| **Frontend** | Streamlit, Pandas |
| **Backend** | FastAPI, Uvicorn, Requests |
| **Model** | CodeLLaMA-7B (QLoRA fine-tuned, GGUF) |
| **Database** | SQLite |
| **ETL** | Python + Qualtrics API |
| **Runtime** | Local Environment (CPU-only) |

---

## Outcome  

✅ Delivered cross-hierarchy behavioral insights on **10+ leadership constructs**  
✅ Achieved **92% query translation accuracy** on validation data  
✅ Reduced manual SQL dependency by **>90%**  
✅ Dashboard ready for company-wide integration at ISB  

---

## Author  

**Hritvija Singh**  
B.Tech, Indian Institute of Technology Kanpur  
📧 [hritvijasi22@iitk.ac.in](mailto:hritvijasi22@iitk.ac.in)  
🌐 [GitHub: Hritvija](https://github.com/Hritvija)
