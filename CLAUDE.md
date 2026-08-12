# CLAUDE.md

## What this is
A single-notebook local RAG pipeline that answers ML questions from 5 research PDFs (ML_1.pdf-ML_5.pdf). Runs fully on-device via Ollama — no external API calls.

## Stack
- Loading: PyPDFLoader (langchain_community.document_loaders)
- Chunking: RecursiveCharacterTextSplitter, chunk_size=1200, chunk_overlap=150 — produced 2,127 chunks across the 5 PDFs. Don't change these without checking chunk count and re-running validation (Part 9), retrieval quality was tuned against these numbers.
- Embeddings: HuggingFaceEmbeddings, sentence-transformers/all-MiniLM-L6-v2 (384-dim vectors)
- Vector store: ChromaDB, persisted locally
- Retrieval: MMR, k=5, lambda_mult=0.7 — lower lambda if answers feel repetitive, higher if they feel unfocused
- Generation: phi3:mini via Ollama, temperature=0.2 (deliberately low for deterministic, factual output — don't raise this for "more natural" answers)

## Before you tell me you're done
Run Part 9 (Answer Validation) on any new or changed output. It checks for:
- Missing citations
- Uncertain/hedging language ("probably," "likely")
- Confidence scoring based on factual grounding
A change that skips this isn't validated, even if the notebook runs top to bottom without errors.

## Conventions
- Every generated answer must carry a source citation (doc/page), matching the format already used (e.g. "[Source Document 1:3]"). Don't return an answer without one.
- Keep everything local — don't swap in a hosted LLM API "temporarily," the whole point of this project is that it runs without external calls.
- Pinned versions matter here (langchain==0.3.27, langchain-community==0.3.29, chromadb==1.0.20, pypdf==6.0.0) — don't casually bump them without checking the pipeline still runs end to end.

## Known rough edges
- This is notebook-based, so stale cell state is the most likely way something looks correct but isn't. Always rerun from a clean kernel before validating.
