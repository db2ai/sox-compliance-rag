**SOX Compliance RAG Pipeline**
---------------------------------------------------------------------------------------------------------------------

This is a personal learning project where I’m combining my background as an Oracle DBA (16+ years) with my current journey into AI and LLMs.
The goal: build a Retrieval-Augmented Generation (RAG) pipeline that not only answers questions from documents, but also does so in a way that feels closer to enterprise compliance standards (like SOX) — with audit trails, tamper-evidence, and reproducibility.

**Why I’m Building This**
---------------------------------------------------------------------------------------------------------------------

Most RAG demos show you how to stuff documents into a vector store and ask questions. That’s fine for experiments, but in the real world (especially in regulated industries) we also need to think about:
```
 1. Audit logs: Who asked what, and what evidence was used to answer?
 2. Tamper-evidence: How do I know the documents weren’t changed after ingestion?
 3. Reproducibility: Can I re-create the exact same answer tomorrow, with proof?
 4. Hybrid search: Sometimes keyword (lexical) search is more precise than semantic embeddings — so why not use both?
```
This project is my way of showing how a DBA mindset (data integrity, indexing, compliance) can add value to modern AI systems.

**What This Project Does**
---------------------------------------------------------------------------------------------------------------------
```
 1. Document ingestion → PDFs, text files, or database extracts
 2. Hashing & manifests → SHA256 checksums so source files can’t be silently changed
 3. Chunking → split text into 500–1000 token windows with overlap
 4. Vector embeddings → using sentence-transformers stored in ChromaDB
 5. Lexical search → using SQLite FTS5 (BM25 ranking)
 6. Hybrid retrieval → combine semantic + lexical results
 7. Re-ranking → improve relevance with a cross-encoder
 8. LLM answer generation → OpenAI API (for now, to keep it lightweight)
 9. Audit logging → every query + response is logged with model version and retrieved chunks
 10. Evidence bundles → package up manifests + indexes so answers can be re-verified later
```
**Tech Stack**
---------------------------------------------------------------------------------------------------------------------
```
 1. LangChain (orchestration)
 2. ChromaDB (vector store)
 3. SQLite FTS5 (lexical search) 
 4. SentenceTransformers for embeddings 
 5. OpenAI API for answer generation
 6. Flask for a simple web UI (WIP) 
 7. Python 3.12
```
**Project Structure**
---------------------------------------------------------------------------------------------------------------------

```
.
├── ingest/ # Ingestion and hashing
├── index/ # Chroma + SQLite indexes
├── retriever/ # Hybrid retrieval + reranking
├── audit/ # Logs and evidence bundles
├── server/ # Flask/FastAPI UI (WIP)
├── tests/ # Unit tests
├── main.py # Entry point
└── README.md
```

**Current Status**
---------------------------------------------------------------------------------------------------------------------
```
Completed
----------
Repo initialized --Done
Project skeleton in place -- Done

Yet to be completed
-------------------
Baseline pipeline with Chroma + SQLite hybrid search -- To be Done
Audit logging and evidence bundle export -- -- To be Done
Simple Flask UI -- To be Done
```
**Next Steps**
---------------------------------------------------------------------------------------------------------------------
```
Add role-based access filters (RBAC)
Automate nightly re-indexing
Record a demo video (ingest → query → audit log → evidence bundle)
```
**License**
---------------------------------------------------------------------------------------------------------------------
MIT License — free to use, adapt, and share.







