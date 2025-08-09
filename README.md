# 🤖 ZAKI - Hybrid RAG-Based Zakat Consultation Chatbot

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![RAG](https://img.shields.io/badge/LLM-RAG-orange?logo=openai)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Development-yellow)

**ZAKI** is an intelligent chatbot for **zakat information & consultation Islamic**.  
Powered by **Hybrid Retrieval-Augmented Generation (RAG)** with a **knowledge base** from the **Qur’an** and official BAZNAS documents, ZAKI can answer questions with **high accuracy, trusted sources, and automated zakat calculations**.

---

## ✨ Key Features
- 🔍 **Hybrid Search** — Combines *semantic search* and *keyword search* for more relevant results.
- 📚 **Official Knowledge Base** — Sources from the Qur’an (translation), MUI fatwas, and official BAZNAS documents.
- 📊 **Automatic Zakat Calculator** — Instantly calculates zakat for wealth, trade, agriculture, etc.
- 🌐 **Indonesian & Islamic Context** — NLP model optimized for Bahasa Indonesia and zakat terminology.
- 🛡 **Safe Content** — Source filtering & validation to ensure compliance with Islamic principles.
- ⚡ **Web Integration** — Ready to integrate into the BAZNAS website.

---

## 🏗 Architecture
- **Retriever:** FAISS + BM25
- **LLM Reranker:** IndoBERT + Cross-Encoder
- **Generator:** OpenAI / Local LLM
- **Knowledge Store:** Supabase PostgreSQL (embeddings + metadata)

---

## 📂 Dataset
This project uses two main datasets:

| Dataset                | Description |
|------------------------|-------------|
| `quran_zaki_rows.csv`  | Qur’anic verses related to zakat (translation & references) |
| `baznas_docs_rows.csv` | Regulatory documents, zakat guidelines, MUI fatwas, and official BAZNAS data |

The datasets are embedded using **IndoBERT**.

---

## 📊 Evaluation
The model is evaluated using **RAGAS** with the following metrics:
- **Faithfulness** — Answers are consistent with the retrieved sources.
- **Answer Relevancy** — Answers are relevant to the given question.
- **Context Recall** — The retrieved context is sufficiently complete.
- **Context Precision** — The retrieved context is highly relevant.

---

## 📊 Detailed Evaluation Method (Upcoming)
System evaluation is conducted using **[RAGAS](https://github.com/explodinggradients/ragas)** (Retrieval-Augmented Generation Assessment Suite) to objectively measure RAG system quality.

### 📏 Metrics Used
1. **Faithfulness**  
   Measures how well the answer aligns with the retrieved context.  
   *Method:* Compares the answer content with retrieved document chunks to detect hallucinations.

2. **Answer Relevancy**  
   Measures the relevance of the answer to the user’s question.  
   *Method:* Embedding similarity between question and answer.

3. **Context Recall**  
   Measures the completeness of the retrieved context from the knowledge base.  
   *Method:* Compares retrieved context to the ground truth context.

4. **Context Precision**  
   Measures the accuracy of the retrieved context — whether it is truly relevant to the question.  
   *Method:* Calculates the proportion of relevant context to total retrieved context.

5. **Answer Semantic Similarity (Optional)**  
   Measures the semantic similarity between the model’s answer and the ideal answer (*ground truth*).

---
