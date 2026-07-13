# RAG
“Retrieval-Augmented Generation project on Machine Learning PDFs.”

# 🎓 RAG Work– Chandana R

## 🧠 Objective
To build a Retrieval-Augmented Generation (RAG) system capable of answering questions about Machine Learning using uploaded PDF research materials.

## 🧩 Models Used
- **LLM:** phi3:mini via Ollama
- **Embeddings:** sentence-transformers/all-MiniLM-L6-v2
- **Vector Store:** ChromaDB
- **Retriever:** Maximum Marginal Relevance (MMR)

## 📚 Data
Five Machine Learning PDFs covering topics such as supervised learning, reinforcement learning, and bias-variance tradeoff.

## ⚙️ Workflow
1. PDF Loading and Text Extraction  
2. Text Chunking (chunk size 1200, overlap 150)  
3. Embedding Creation using MiniLM  
4. Vector Storage using Chroma  
5. Retrieval (MMR strategy)  
6. LLM Integration via Ollama (phi3:mini)  
7. Answer Generation and Validation  

## 💬 Example Question
**Q:** What is supervised learning?  
**A:** “ Supervised learning is a type of machine learning that involves training an artificial system using examples provided by a knowledgeable external supervisor". 
(Source : "Overview of Supervised Learning" on page 9 and section 2.6 )

**Q:** Explain the concept of reinforcement learning and its main elements.
**A:**  
"Reinforcement learning is a type of machine learning that focuses on how agents ought to take actions in an environment so as to maximize some notion of cumulative reward. It's characterized by three main elements, which are essential for understanding the framework" (Source Document 1:3).  



## 🧾 Files Included
- `CHANDANA_R_RAG_WORKSHOP.ipynb` — Main Jupyter Notebook  
- `ML_1.pdf` → `ML_5.pdf` — Data sources  

## 🔗 Notes
All models run locally using Ollama. If any file exceeded GitHub’s 100 MB limit, it is shared separately through cloud storage.
