# Comparative Analysis of LLMs for an Austrian Law Assistant

## Overview
This repository contains the code and resources for the project **"Comparative Analysis of Claude 4.5 Haiku, Fine-Tuned SBERT XLM ROBERTa, and Mistral RAG for an Austrian Law Assistant."** It was developed for the Applications of Data Science course at the Vienna University of Economics and Business (WU Vienna).

## Project Description
The project evaluates and compares different Large Language Model (LLM) architectures for retrieving and answering queries based on Austrian tax law cases. 

### Models Evaluated:
1. **Claude 4.5 Haiku (API):** Served as the highly-performant baseline model (greedy encoding, zero-shot).
2. **Mistral 7B Instruct v0.1:** A local open-source model run with 4-bit quantization using Unsloth.
3. **SBERT Legal XLM ROBERTa Base:** A Hugging Face model fine-tuned specifically on Austrian legal data.

### Methodology:
* **Data Collection:** Sourced ~7,500 legal cases from the Austrian open government database (`data.bka.gv.at`) via API, focusing on various tax laws (e.g., EStG, ASVG, BAO, DBA, GrEStG, KStG, UStG).
* **Fine-Tuning:** The SBERT XLM ROBERTa model was fine-tuned using Multiple Negative Ranking Loss to align legal case facts with their specific paragraph citations.
* **RAG Architecture:** Built a Retrieval-Augmented Generation (RAG) system using FAISS for indexing paragraph citations, the fine-tuned SBERT model for retrieval, and Mistral 7B for answer generation.

## Evaluation Metrics
The models were tested on citation extraction and text generation using the following metrics:
* **Citation Recall:** Measures the exact retrieval of the correct legal citation format.
* **BLEU Score:** Evaluates exact n-gram vocabulary matching.
* **ROUGE-L (F1):** Measures logical word structure and longest common subsequence.
* **BERTScore (F1):** Assesses the underlying semantic meaning and equivalence.

## Key Results
* **Claude 4.5 Haiku** achieved the best overall generative performance across semantic metrics (BERTScore: 72.14%).
* **Mistral RAG System** achieved the highest Citation Recall (3.20%), outperforming the larger baseline model in exact citation retrieval.

## Tech Stack
* **Python**
* **Hugging Face Transformers & Sentence-Transformers**
* **Unsloth & bitsandbytes** (for 4-bit quantization)
* **FAISS** (Facebook AI Similarity Search)

## Author
**Hanka Jankovicova**
