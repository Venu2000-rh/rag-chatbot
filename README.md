# RAG Chatbot — Open-Source LLM Stack

An end-to-end Retrieval-Augmented Generation (RAG) chatbot built entirely on
open-source Hugging Face models — no paid LLM APIs required.

🔗 **[View the project walkthrough](https://Venu2000-rh.github.io/rag-chatbot/)**

## What it does

Given a set of documents, the chatbot answers natural-language questions
grounded in that content — retrieving the most relevant passages before
generating an answer, rather than relying purely on the LLM's own training
data. This reduces hallucination and lets the system answer questions about
documents it has never seen before.

## How it works

1. **Chunking** — source documents are split into overlapping text chunks
2. **Embedding** — each chunk is encoded into a vector using `sentence-transformers/all-MiniLM-L6-v2`
3. **Indexing** — embeddings are loaded into a FAISS vector index for fast similarity search
4. **Retrieval** — a user's question is embedded and matched against the index to find the most relevant chunks
5. **Generation** — retrieved chunks are passed as context to `Qwen2.5-1.5B-Instruct`, with a system-level prompt and greedy decoding to keep answers grounded in the retrieved context

## Tech stack

- Python, Jupyter Notebook
- Hugging Face `transformers`, `sentence-transformers`
- FAISS (vector similarity search)
- `Qwen/Qwen2.5-1.5B-Instruct` (open-source LLM)

## Running it

Open `RAG_Chatbot_OpenSource.ipynb` in Jupyter or Google Colab and run all
cells top to bottom. See the notebook's markdown cells for details on
supplying your own documents.

## Why I built this

Built to understand the full RAG pipeline hands-on — from chunking through
retrieval to grounded generation — using only open-source models, after
seeing how a data pipeline I worked on in a professional context fed a
production RAG system.
