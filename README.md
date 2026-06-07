# RAG Implementation

An end-to-end Retrieval-Augmented Generation (RAG) application that ingests local documents, converts them into embeddings, stores them in a FAISS vector index, and answers questions with a Groq-powered LLM.

This project is designed to demonstrate practical AI engineering skills: document ingestion, semantic search, vector databases, LLM orchestration, dependency management, and resilient application design.

## Key Note Snapshot

- Built a full RAG pipeline from raw files to grounded answers.
- Supports multiple data sources, including PDFs, text files, and CSVs.
- Uses sentence embeddings and FAISS for fast semantic retrieval.
- Integrates Groq models for context-aware summarization and Q&A.
- Includes fallback logic to build the vector store automatically when it is missing.

## What Problem It Solves

Large language models are strong at generation, but they are only useful for specific business or knowledge-base use cases when they can answer from trusted source documents. This project solves that by retrieving the most relevant chunks from local data and passing them into the LLM as context.

## Core Capabilities

- Document ingestion from the `data/` folder.
- Recursive text chunking for improved retrieval quality.
- Embedding generation with `all-MiniLM-L6-v2`.
- Vector storage and similarity search with FAISS.
- Query-based retrieval of the most relevant document chunks.
- LLM-based summarization and question answering using Groq.

## Why It Stands Out

- Shows end-to-end implementation ability, not just model usage.
- Demonstrates applied NLP, search, and retrieval engineering.
- Handles real-world issues like missing indexes, package compatibility, and environment setup.
- Structured in a clean, modular way that is easy to extend or productionize.

## Tech Stack

- Python
- LangChain
- Sentence Transformers
- FAISS
- Groq API
- PyPDF, PyMuPDF, CSV loaders

## Architecture

1. Load documents from local files.
2. Split content into smaller chunks.
3. Generate embeddings for each chunk.
4. Store vectors in FAISS.
5. Retrieve relevant chunks for a user query.
6. Send retrieved context to the LLM for the final answer.

## Project Structure

- `app.py` - application entrypoint
- `src/data_loader.py` - loads documents from the dataset folder
- `src/embedding.py` - chunks documents and creates embeddings
- `src/vectorstore.py` - builds, saves, loads, and queries the FAISS index
- `src/search.py` - connects retrieval with the LLM response flow
- `data/` - source documents and persisted vector store assets

## Recruiter-Ready Impact

- Built a modular AI application with clear separation of concerns.
- Solved integration issues across LangChain, FAISS, and Groq.
- Added automatic vector-store bootstrap behavior for a smoother first run.
- Created a reusable foundation for internal knowledge search, document Q&A, and enterprise RAG use cases.

## Setup

1. Activate the virtual environment.

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies.

```powershell
pip install -r requirements.txt
```

3. Add your Groq API key to a `.env` file.

```env
GROQ_API_KEY=your_api_key_here
```

4. Run the application.

```powershell
python app.py
```

## Notes

- The first run may take time because embeddings are generated and the FAISS index is created.
- If the index already exists, the app loads it directly.
- Use the project virtual environment to avoid dependency mismatch issues.