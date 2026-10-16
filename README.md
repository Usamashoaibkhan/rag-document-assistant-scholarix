# 🔎 RAG Document Assistant Scholarix

<p align="center">
  <img src="https://img.shields.io/badge/Python-Based%20Project-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python-Based Project" />
  <img src="https://img.shields.io/badge/RAG-Document%20Q%26A-7C3AED?style=for-the-badge" alt="RAG Document Q&A" />
  <img src="https://img.shields.io/badge/LLM-Groq-F55036?style=for-the-badge" alt="Groq" />
  <img src="https://img.shields.io/badge/Vector%20Database-ChromaDB-0891B2?style=for-the-badge" alt="ChromaDB" />
</p>

<p align="center">
  <strong>A Python-Based Retrieval-Augmented Generation (RAG) Application</strong>
</p>

<p align="center">
  Ask questions about machine-learning research papers and get AI-generated answers grounded in retrieved document content, with source references.
</p>

---

## 📌 Project Summary

**RAG Document Assistant** is a Python-based AI project that uses Retrieval-Augmented Generation (RAG) to answer questions from a collection of machine-learning research papers.

It combines semantic search, locally generated embeddings, a ChromaDB vector database, and the Groq API to retrieve relevant information and generate context-based answers. The application is designed to avoid unsupported answers when the retrieved context does not contain sufficient information.

## 🛠️ Technologies Used

<p align="center">
  <img src="https://skillicons.dev/icons?i=python" height="60" alt="Python" />
  &nbsp;&nbsp;&nbsp;
  <img src="https://cdn.simpleicons.org/langchain/1C3C3C" height="48" alt="LangChain" />
  &nbsp;&nbsp;&nbsp;
  <img src="https://cdn.simpleicons.org/groq/F55036" height="48" alt="Groq" />
  &nbsp;&nbsp;&nbsp;
  <img src="https://cdn.simpleicons.org/huggingface/FFD21E" height="48" alt="Hugging Face" />
</p>

<p align="center">
  <strong>Python · LangChain · Groq · Sentence Transformers · ChromaDB</strong>
</p>

| Technology | Purpose |
|---|---|
| Python 3.11 | Main programming language |
| LangChain | RAG pipeline orchestration |
| Groq API | Language-model inference |
| `openai/gpt-oss-20b` | Configured language model |
| Sentence Transformers | Local text embeddings |
| ChromaDB | Vector storage and semantic search |

## ✨ Key Features

- 📚 **Document-based Q&A:** Ask natural-language questions about indexed research papers.
- 🔍 **Semantic Search:** Retrieve relevant passages based on meaning.
- 🧠 **Retrieval-Augmented Generation:** Generate answers using retrieved document context.
- 📌 **Source References:** Include paper-title references to help trace answers.
- 🛡️ **Grounding-First Design:** Designed to avoid guessing when relevant evidence is insufficient.
- ⚡ **Local Embeddings:** Generate document and query embeddings locally.
- 🔧 **Modular Python Code:** Keep ingestion, retrieval, and application logic in separate modules.

## ⚙️ How It Works

<p align="center">
  <img src="https://img.shields.io/badge/1-Document%20Ingestion-2563EB?style=for-the-badge" alt="Document Ingestion" />
  <img src="https://img.shields.io/badge/2-Text%20Embeddings-7C3AED?style=for-the-badge" alt="Text Embeddings" />
  <img src="https://img.shields.io/badge/3-Semantic%20Retrieval-0891B2?style=for-the-badge" alt="Semantic Retrieval" />
  <img src="https://img.shields.io/badge/4-AI%20Answer-059669?style=for-the-badge" alt="AI Answer" />
</p>

1. **Ingest documents:** Load research papers and split their text into smaller chunks.
2. **Generate embeddings:** Convert document chunks into numerical vectors using Sentence Transformers.
3. **Store vectors:** Save embeddings and associated document information in ChromaDB.
4. **Retrieve context:** Convert the user's question into an embedding and retrieve relevant chunks.
5. **Generate an answer:** Send the retrieved context to the configured Groq language model to generate a response with source references.

> **Core idea:** Retrieve relevant evidence first, then generate an answer based on that evidence instead of relying only on the language model's general knowledge.

## 🏗️ Project Structure

```text
rag-document-assistant-scholarix/
│
├── src/
│   └── rag_documentassistant/
│       ├── __init__.py
│       ├── app.py          # Question-answering application
│       ├── ingest.py       # Document ingestion and indexing
│       └── rag.py          # Retrieval and generation logic
│
├── evals/
│   └── run_evals.py        # Evaluation script
│
├── requirements.txt        # Python dependencies
├── pyproject.toml          # Project configuration
├── .python-version         # Python version
├── .gitignore
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- Python 3.11
- Internet connection for installing dependencies and calling the Groq API
- A Groq API key from [Groq Console](https://console.groq.com/)

### 1. Clone the Repository

```bash
git clone https://github.com/Usamashoaibkhan/rag-document-assistant-scholarix.git
cd rag-document-assistant-scholarix
```

### 2. Create a Virtual Environment

**Windows PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Configure the API Key

Create a `.env` file in the project root and add your Groq API key:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Replace the placeholder with your actual key.

**Security:** Never upload your `.env` file or expose your API key in public repositories.

### 5. Ingest and Index Documents

```bash
python -m src.rag_documentassistant.ingest
```

This command processes the available document corpus, creates embeddings, and saves the vector index. The first run may take a few minutes.

### 6. Run the Application

```bash
python -m src.rag_documentassistant.app
```

Start asking questions about the indexed research papers and inspect the generated answers and source references.

## 📊 Evaluation

The project includes an evaluation script for assessing the RAG workflow.

```bash
python evals/run_evals.py
```

Use the evaluation results to investigate retrieval quality and answer generation. Actual performance depends on the evaluation dataset, retrieval settings, and model responses.

## 🔐 Privacy and Cost Considerations

- **Local processing:** Document embeddings are generated locally.
- **External inference:** Retrieved context is sent to the configured Groq API for answer generation.
- **API usage:** Generation requires a working API key and is subject to provider availability and usage limits.
- **Secret management:** Keep API keys and other credentials out of source control.

## 🔮 Future Improvements

- 📄 Upload custom PDF and research documents.
- 🌐 Add a web-based chat interface.
- 📑 Display page numbers and direct document references.
- 📈 Expand retrieval and answer-quality evaluations.
- 🗂️ Support document collection management and index updates.

## 👨‍💻 Author

**Usama Shoaib**

GitHub: [@Usamashoaibkhan](https://github.com/Usamashoaibkhan)


---

<p align="center">
  <strong>Built with Python, Semantic Search, and Retrieval-Augmented Generation.</strong>
</p>
