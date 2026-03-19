# 🍕 RAG Review AI Assistant

> **Ask questions about restaurant reviews — answered by a local AI that actually read them.**  
> A fully offline RAG (Retrieval-Augmented Generation) pipeline powered by LangChain, ChromaDB, and Llama 3.1.

![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat&logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-Framework-1C3C3C?style=flat)
![Ollama](https://img.shields.io/badge/Ollama-Local%20LLM-black?style=flat)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector%20Store-orange?style=flat)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat)

---

## 🧠 What is this?

**RAG Review AI Assistant** is a terminal-based AI chatbot that answers natural language questions about a restaurant using real customer reviews as its knowledge base.

Instead of fine-tuning a model or hardcoding answers, it uses **Retrieval-Augmented Generation (RAG)** — a technique where relevant reviews are fetched from a vector database and passed as context to a local LLM, which then generates a grounded, accurate response.

Everything runs **100% locally** — no OpenAI API key, no internet, no cost.

---

## ✨ Features

- 💬 **Natural language Q&A** — ask anything: *"Is the pizza good?"*, *"How's the service?"*, *"What do people say about delivery?"*
- 🔍 **Semantic search** — retrieves the most relevant reviews using vector similarity, not keyword matching
- 🦙 **Llama 3.1 powered** — runs the Llama 3.1 LLM locally via Ollama
- 🗄️ **Persistent vector store** — ChromaDB saves embeddings to disk so you only embed once
- 📊 **Review metadata** — each retrieved review carries its rating and date
- 🔒 **Fully offline** — zero external API calls, all models run on your machine

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| **LLM** | Llama 3.1 (via Ollama) |
| **Embeddings** | mxbai-embed-large (via Ollama) |
| **RAG Framework** | LangChain |
| **Vector Store** | ChromaDB (persistent, local) |
| **Data** | Pandas (CSV ingestion) |
| **Interface** | Terminal / CLI |

---

## 🔬 How It Works

```
realistic_restaurant_reviews.csv
        │
        ▼
  Pandas loads reviews
  (Title + Review text, Rating, Date)
        │
        ▼
  Ollama embeds each review
  using mxbai-embed-large
        │
        ▼
  ChromaDB stores vectors
  persistently on disk
        │
        ▼
  User asks a question (CLI)
        │
        ▼
  ChromaDB retrieves Top-5
  most semantically similar reviews
        │
        ▼
  LangChain passes reviews + question
  to Llama 3.1 via prompt template
        │
        ▼
  Llama 3.1 generates a
  context-grounded answer
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- [Ollama](https://ollama.com) installed and running

### 1. Pull the required models via Ollama

```bash
ollama pull llama3.1
ollama pull mxbai-embed-large
```

### 2. Clone the repository

```bash
git clone https://github.com/Corerishi/RAG-Review-AI-Assistant.git
cd RAG-Review-AI-Assistant
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the assistant

```bash
python main.py
```

The first run will embed all reviews and build the ChromaDB vector store. Subsequent runs load it from disk instantly.

---

## 💬 Example Usage

```
---------------------------------------
Ask your question (q to quit): Is the pizza here worth it?

Based on the reviews, customers consistently praise the pizza for its
crispy crust and generous toppings. Several reviewers mention the
Margherita and Pepperoni as standout options. A few reviews note
slightly long wait times during weekends but agree the quality
makes it worthwhile.
```

---

## 📁 Project Structure

```
RAG-Review-AI-Assistant/
├── main.py                          # LangChain RAG chain + CLI interface
├── vector.py                        # ChromaDB vector store setup + embeddings
├── realistic_restaurant_reviews.csv # Source review dataset
├── chroma_langchain_db/             # Persistent vector store (auto-created)
├── requirements.txt
└── README.md
```

---

## 📦 Key Dependencies

```
langchain
langchain-ollama
langchain-chroma
chromadb
pandas
```

---

## 📚 Concepts Demonstrated

- **RAG (Retrieval-Augmented Generation)** pipeline from scratch
- **Vector embeddings** and semantic similarity search
- **Local LLM inference** with Ollama (no cloud dependency)
- **Persistent vector stores** with ChromaDB
- **LangChain** prompt templates and chain composition

---

## 👨‍💻 Author

**Rishi Raj**  
MCA — CHRIST (Deemed to be University)  
[LinkedIn](https://linkedin.com/in/rishi-raj-9110a824a) · [GitHub](https://github.com/Corerishi)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
