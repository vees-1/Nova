# 🔹 MERCURY
## 🔹 Cold-Start Recommendation Engine for Ecommerce


  <img src="https://img.shields.io/badge/ML-Two--Tower-blueviolet" />
  <img src="https://img.shields.io/badge/Inference-FAISS-success" />
  <img src="https://img.shields.io/badge/API-FastAPI-009688" />
  <img src="https://img.shields.io/badge/Infra-Zero--Cost-orange" />
  <img src="https://img.shields.io/badge/Status-Production--Ready-brightgreen" />




## 🔹 Executive Summary

**MERCURY** is a **low-latency, hybrid recommendation system** built to solve one of the hardest real-world machine learning problems:  
👉 **Cold-start users and products in ecommerce**.

Traditional collaborative filtering systems collapse when historical interaction data is missing.  
MERCURY avoids this failure mode by using a **Two-Tower Neural Network** to generate semantic embeddings from **item metadata and user context**, enabling relevant recommendations from the very first interaction.

The system is intentionally designed to run on **zero-cost infrastructure** using open-source tools—prioritizing **scalability, reproducibility, and vendor independence**.



## 🔹 Problem Statement

### 🔹 The Core Issue
Most recommender systems rely on historical signals such as clicks, purchases, or ratings.

This leads to two critical failures:
- ❌ New users receive irrelevant recommendations
- ❌ Newly added products are invisible to the system

### 🔹 The Insight
MERCURY reframes recommendation as a **geometric similarity problem**.

> Users and items are embedded into a shared vector space where semantic similarity corresponds to spatial proximity.

This approach enables meaningful recommendations **even when no interaction history exists**.



## 🔹 System Architecture  
### 🔹 The “Zero-Dollar” ML Stack

MERCURY is decoupled into independent layers, mirroring production recommender system design.

User Context

↓

User Tower (Embedding)

↓

Vector Retrieval (FAISS)

↓

Top-K Candidate Items

↓

API Response




### 🔹 A. Data & Training (Offline Layer)

- **Environment:** Google Colab (Free Tier, GPU-enabled)
- **Framework:** PyTorch
- **Model:** Two-Tower Neural Network  
  - User Tower  
  - Item Tower
- **Input Features:**
  - Product text embeddings (BERT)
  - Normalized price
  - User context (device, location, time)
- **Artifacts Produced:**
  - `model.pt` – trained neural model
  - `items.faiss` – item embedding index



### 🔹 B. Retrieval Engine (Online Layer)

- **Vector Search:** FAISS (in-memory)
- **Similarity Metric:** Dot product similarity
- **Latency Target:**  
  ⚡ **< 20ms** for Top-100 retrieval from a 10k item catalog

This layer ensures efficient candidate generation without repeated model inference.



### 🔹 C. API & Serving (Interface Layer)

- **Framework:** FastAPI (asynchronous)
- **Hosting:** Render (Free Tier) or Hugging Face Spaces
- **Endpoint:**
```http
POST /recommend

