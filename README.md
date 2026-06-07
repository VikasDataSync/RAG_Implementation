# RAG Implementation

An end-to-end Retrieval-Augmented Generation (RAG) project that ingests PDFs, text files, and CSV data, converts content into embeddings, stores them in a FAISS vector index, and answers questions with a Groq-powered LLM.

## Why this project stands out

- Demonstrates a complete RAG pipeline from ingestion to grounded answer generation.
- Uses semantic search over local documents instead of relying on generic model memory.
- Handles multiple file types and automatically builds the vector store when needed.
- Combines practical NLP, vector search, and LLM orchestration in one runnable application.

## What it does

- Loads documents from the `data/` directory.
- Splits long documents into chunks for better retrieval quality.
- Generates sentence embeddings with `all-MiniLM-L6-v2`.
- Stores and searches vectors with FAISS.
- Retrieves the most relevant chunks for a user query.
- Sends retrieved context to Groq for a concise summary or answer.

## Tech Stack

- Python
- LangChain
- Sentence Transformers
- FAISS
- Groq API
- PyPDF, PyMuPDF, CSV and text loaders

## Project Structure

- `app.py` - entrypoint that runs the search and summarization flow
- `src/data_loader.py` - loads documents from the dataset folder
- `src/embedding.py` - chunks documents and creates embeddings
- `src/vectorstore.py` - builds, saves, loads, and queries the FAISS index
- `src/search.py` - combines retrieval with the LLM response generation
- `data/` - source documents and the saved vector store

## Recruiter Highlights

- Built a production-style RAG workflow with clear separation of responsibilities.
- Solved dependency and compatibility issues across LangChain, FAISS, and Groq.
- Added fallback behavior so the app can build its own vector store when the index is missing.
- Designed the system to support local knowledge bases and domain-specific Q&A.

## Setup

1. Create and activate the virtual environment.

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

4. Run the app.

```powershell
python app.py
```

## Example Output

The app retrieves relevant content from the vector store and generates a grounded answer for the query.

## Notes

- The first run may take time because embeddings are generated and the FAISS index is built.
- If the vector store already exists, the app loads it directly.
- Use the project virtual environment when running the app to avoid missing-package errors.