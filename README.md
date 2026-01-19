<div align="center">

# NOVA 
Neural Online Vector-based Architecture


A production-style cold-start recommendation system built using neural embeddings and fast vector retrieval.


<sub>
<p>
  <img src="https://img.shields.io/badge/ML-Two--Tower-blueviolet" />
  <img src="https://img.shields.io/badge/Inference-FAISS-success" />
  <img src="https://img.shields.io/badge/API-FastAPI-009688" />
  <img src="https://img.shields.io/badge/Infra-Zero--Cost-orange" />
  <img src="https://img.shields.io/badge/Status-Active%20Development-yellow" />
</p>
</sub>

</div>



## 🔹 Overview

*NOVA* is a low-latency recommendation system designed specifically for *cold-start ecommerce scenarios*, where historical user interaction data (clicks, purchases, ratings) is *unavailable or sparse*.

Instead of relying on past behavior, NOVA:
- Represents users and products as vectors in a shared embedding space
- Uses *semantic similarity* to identify relevant items
- Retrieves recommendations using fast vector search, enabling *real-time inference*


## 🔹 Problem

Most traditional recommender systems depend on historical interactions.

They fail when:
- 🆕 A user visits the platform for the first time
- 🆕 A product is newly added to the catalog
- 🆕 There is insufficient interaction data

These failure modes result in:
- Poor personalization
- Reduced engagement
- Missed conversions


## 💡 Core Idea

NOVA reframes recommendation as a *vector similarity problem*.

If a user vector is *close* to a product vector in embedding space, the product is relevant.

This approach allows NOVA to generate meaningful recommendations from the very first interaction, without relying on user history.


## 🔹 Architecture Components

### 🔹 Model 
- Two-Tower Neural Network (User Tower + Item Tower)
- PyTorch-based training
- Text embeddings from product descriptions
- Outputs fixed-size vectors for users and items

### 🔹 Retrieval
- FAISS in-memory vector index
- Dot-product similarity search
- Optimized for low-latency top-K retrieval

### 🔹 API
- FastAPI backend
- `/recommend` endpoint
- Accepts user context JSON
- Returns ranked product recommendations


## 🔹 Tech Stack
<p>
  <img src="https://img.shields.io/badge/Language-Python-3776AB?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/ML-PyTorch-EE4C2C?logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/NLP-HuggingFace-FFD21E?logo=huggingface&logoColor=black" />
  <img src="https://img.shields.io/badge/Vector%20Search-FAISS-success" />
  <img src="https://img.shields.io/badge/API-FastAPI-009688?logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Frontend-Vanilla%20JS-lightgrey" />
</p>


## 🔹 Goals

- ✅ Handle cold-start users and products gracefully
- ✅ Maintain low inference latency
- ✅ Ensure reproducibility and clean system boundaries
- ✅ Prioritize engineering correctness over model complexity
- ✅ Build a deployable, end-to-end ML system

## 🔹 Status

🚧 Currently under active development




