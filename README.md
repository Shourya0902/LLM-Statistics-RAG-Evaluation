# Can Large Language Models Learn Statistics? A RAG Experiment

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![GenAI](https://img.shields.io/badge/GenAI-RAG-orange)
![LLM](https://img.shields.io/badge/LLM-Llama%20%7C%20DeepSeek%20%7C%20Qwen-green)

## 📄 Abstract
This project investigates whether Large Language Models (LLMs) genuinely "learn" and integrate new statistical concepts when provided with external textbooks via **Retrieval Augmented Generation (RAG)**, or if they suffer from information interference. 

Using a **$2\times3$ factorial design**, I evaluated three distinct model architectures (General purpose, Reasoning-optimized, and Math-specialized) across 50 graduate-level statistics questions. The study utilizes an **"LLM-as-a-Judge"** evaluation framework to assess Correctness, Explanation Quality, and Understanding.

> **Full Dissertation:** [Read the full paper here](./dissertation.pdf)

## 🛠️ Tech Stack & Methodology

### The RAG Pipeline
I built a custom RAG pipeline optimized for mathematical density using semantic evaluation metrics.
* **Vector Database:** ChromaDB (Persistent storage)
* **Embeddings:** `all-mpnet-base-v2` (Sentence Transformers)
* **Reranking:** Cross-Encoder (`ms-marco-MiniLM-L-6-v2`) for improved relevance.
* **Chunking Strategy:** Optimized via grid search to 256 tokens with 200 overlap.
* **Models Tested:** LLaMA 3.2 8B, DeepSeek-R1 8B, Qwen2-Math 7B.

### Experimental Design
The experiment compares **Baseline Performance** (parametric knowledge only) vs. **RAG Performance** (access to 7 authoritative statistics textbooks).

### Evaluation Framework (LLM-as-a-Judge)
To ensure scalable and objective grading, I implemented an automated evaluation pipeline:
1.  **Judge Model:** Gemma-7B (Selected via consensus correlation analysis against Prometheus and Mistral).
2.  **Rubric:** A weighted scoring system:
    * *Correctness (50%)*
    * *Explanation Quality (30%)*
    * *Understanding (20%)*

## 📊 Key Findings
Contrary to the popular hypothesis that RAG always improves performance, this study found **consistent negative learning effects** across all models when handling complex statistical reasoning.

* **Cognitive Conflict:** External context often conflicted with the models' internal reasoning pathways.
* **Specialization Vulnerability:** The math-specialized model (**Qwen2-Math**) suffered the most significant performance drop, suggesting that highly optimized internal pathways are more easily disrupted by external noise.
* **Implication:** For complex reasoning tasks in STEM, simply "adding RAG" may be counter-productive without conflict-resolution mechanisms.

## 🚀 How to Run the Code

1. **Clone the repository**
   ```bash
   git clone [https://github.com/Shourya0902/llm-statistics-learning.git](https://github.com/yourusername/llm-statistics-learning.git)

2. **Install dependencies**

Bash

pip install -r requirements.txt
Setup Ollama This project uses local LLMs via Ollama. Ensure you have Ollama installed and pull the required models:

Bash

ollama pull llama3.2
ollama pull deepseek-r1:8b
ollama pull qwen2-math

3. **Run the Notebook Open notebooks/experimentation.ipynb to view the full pipeline, from data ingestion to statistical analysis.**

## 👨‍💻 About the Author
Shourya Marwaha MSc Data Science & Analytics (University of Leeds) | MBA (Finance & Analytics) | BTech (Mechanical Engineering)

I am a Data Scientist with a strong foundation in product analytics and machine learning. Previously, I worked as a Product Analyst at GoMechanic (Gurgaon, India), where I utilized data to drive product strategy. I am currently based in the UK and open to full-time opportunities in Data Science and AI.

https://www.linkedin.com/in/shouryamarwaha/ | shouryamarwaha@gmail.com
