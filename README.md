
# Pharmacovigilance Signal Detection Agent 🚨

Early detection of drug safety risks using AI-driven signal detection
to support FDA and WHO analysts in protecting public health.

## Problem Statement

Regulatory agencies like the FDA and WHO receive millions of adverse
event reports every year. Manual review is slow and often detects
safety risks too late, after patients are already harmed.

## Why This Matters

Delayed detection of adverse drug reactions can lead to:
- Patient harm
- Costly drug recalls
- Loss of public trust

Our system acts as an early-warning and prioritization engine for drug safety.


## Solution Overview

1. Ingest FAERS adverse event data
2. Convert reports into embeddings
3. Cluster events to detect emerging patterns
4. Use LLMs to summarize and classify risk
5. Generate a weekly safety dashboard



## Tech Stack

- Python, Pandas
- scikit-learn (DBSCAN / HDBSCAN)
- LLMs (LangChain)
- FAISS / Chroma (Vector DB)
- React + Recharts (Dashboard)

Our Solution

We designed a pipeline that combines data processing, clustering, and LLM-based analysis.

1. Data Collection

We use publicly available adverse event datasets such as:

FAERS (FDA)

WHO-UMC sample data

https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html

From each report, we extract important fields like drug name, reaction, seriousness, patient details, etc.

2. Preprocessing

Before analysis, we:

Clean up drug names

Normalize reaction terms

Create embeddings for text fields

Prepare the data for clustering

3. Clustering

Using scikit-learn algorithms (KMeans, HDBSCAN), we group similar AE reports.
These clusters help us notice:

Rare but severe adverse events

Sharp increases in specific reactions

Unusual drug–event combinations

4. LLM Analysis

We use LangChain agents and an LLM to:

Summarize what each cluster represents

Identify the top safety signals

Assign a simple risk level (Low, Medium, High)

Provide short explanations useful for reviewers

5. Weekly Dashboard

The final output includes:

A JSON file with detected signals and cluster summaries

A text/Markdown report that highlights the most important findings

Clear explanations that non-technical reviewers can understand...

## Sample Output

```json
{
  "drug": "Drug X",
  "signal": "Hepatotoxicity",
  "risk_level": "High",
  "trend": "Increasing"
}


***Note:
The outputs/ and dashboard.json files are generated artifacts and are intentionally not committed to the GitHub repo.
They are created when the pipeline is executed locally from the FAERS data.
This is standard practice in real-world ML / PV systems.
The large datasets are added into gitignore as large datasets aren't accepted by the github.


