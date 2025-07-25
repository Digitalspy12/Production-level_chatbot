# Inovibit RAG PDFBot - (FastAPI + Streamlit)

This is the **production-ready refactor** , introducing a real separation between frontend (UI) and backend (logic) using **Streamlit** and **FastAPI** respectively. This modular architecture helps in scaling, extending, and deploying the bot in real-world environments.

---


---

## 🔄 current state

| Feature|   | SYSTEM |
|--------|-------------|--------------|
| Codebase || Split into `client/` + `server/` |
| PDF Upload ||Async FastAPI API |
| Chat || Calls `/chat` API |
| Vectorstore | | Controlled by backend |
| Model Options|  | Dynamically fetched |
| Inspector | |Main panel toggle |
| Splitting  || `TokenTextSplitter` |
| UX | | Responsive, clear, downloadable |
| Extendability || Easy to plug new LLMs, tools |

---

## 🧪 How It Looks
## 🏗️ Architecture

![architecture](/assets/rag-bot-fastapi-architecture.png)

---

## 🚀 Features

- 📁 Upload multiple PDFs and chat with them
- 🔌 Choose from Groq or Gemini as LLM providers
- 🔎 Query inspector for vectorstore transparency
- 🧠 RAG with LangChain + ChromaDB
- 📦 Streamlit frontend, FastAPI backend
- 🧪 Token-based chunking for LLM precision
- 💬 Downloadable chat history
- 🧰 Tools for reset, undo, clear
- 🌐 Fully API-driven interaction

---

<details>
  <summary>🛠️ Tech Stack</summary>

- **Frontend**: Streamlit
- **Backend**: FastAPI
- **LLMs**: Groq & Gemini via LangChain
- **Vector DB**: ChromaDB
- **Embeddings**: HuggingFace & Google GenAI
- **Chunking**: TokenTextSplitter (was RecursiveCharacterTextSplitter)
- **Parsing**: PyPDF
- **Orchestration**: LangChain Retrieval Chain

</details>

---

## 📦 Installation

```bash

cd rag-bot-fastapi
```

Setup Virtual Environment:
```bash
python3 -m venv venv
source venv/bin/activate
```

Install frontend:

```bash
cd client
pip3 install -r requirements.txt
```

Install backend:

```bash
cd ../server
pip3 install -r requirements.txt
```

---

## 🔐 API Keys Required

- **Groq API key** from [console.groq.com](https://console.groq.com/)
- **Google Gemini API key** from [ai.google.dev](https://ai.google.dev/)

Create a `.env` file:

```env
GROQ_API_KEY=your-groq-key
GOOGLE_API_KEY=your-google-key
```

---

## ▶️ Run the Bot

Start FastAPI backend:

```bash
# Terminal 1
cd server
uvicorn main:app --reload
```

Start Streamlit frontend:

```bash
# Terminal 2
cd client
streamlit run app.py
```

---

<details>
  <summary>📁 Project Structure</summary>

```bash
rag-bot-v3/
├── client/                         # Streamlit Frontend
│   ├── app.py                      # Main Streamlit entrypoint
│   ├── components/                 # UI modules
│   │   ├── chat.py
│   │   ├── inspector.py
│   │   └── sidebar.py
│   ├── state/
│   │   └── session.py              # Session state manager
│   ├── utils/
│   │   ├── api.py                  # Talks to backend
│   │   ├── config.py               # API_URL and config values
│   │   └── helpers.py              # API wrappers for frontend
│   ├── requirements.txt
│   └── README.md

├── server/                         # FastAPI Backend
│   ├── api/
│   │   ├── routes.py               # API endpoints
│   │   └── schemas.py              # Pydantic schemas for I/O
│   ├── core/
│   │   ├── document_processor.py   # Handles PDF validation and chunking
│   │   ├── llm_chain_factory.py    # Builds LLM chains and prompts
│   │   └── vector_database.py      # Embeddings + ChromaDB ops
│   ├── config/
│   │   └── settings.py             # App config, model provider setup
│   ├── utils/
│   │   └── logger.py               # Logging setup
│   ├── main.py                     # FastAPI app entrypoint
│   ├── requirements.txt
│   └── README.md

├── README.md                       # Root README (overview + instructions)
├── .gitignore
```

</details>

---

<details>
  <summary> 👓 Different Views </summary>

| View | Description |
|------|-------------|
| 💬 Chat | Renders chat bubbles, input box, and chat history download |
| 🔬 Inspector | Renders inspector to test vectorstore responses |

![views](/assets/rag-bot-fastapi-clean-ui-ux.gif)

</details>

---

<details>
  <summary>🧼 Tools Panel</summary>

| Button | Function |
|----------|--------|
| 🔄 Reset | Clears session state and reruns app |
| 🧹 Clear Chat | Clears chat + PDF submission |
| ↩️ Undo | Removes last question/response |

</details>

---

<details>
  <summary>📦 Download Chat History</summary>

Chat history is saved in the session state and can be exported as a CSV with the following columns:

| Question | Answer | Model Provider | Model Name | PDF File | Timestamp |
|----------|--------|----------------|------------|---------------------|-----------|
| What is this PDF about? | This PDF explains... | Groq | llama3-70b-8192 | file1.pdf, file2.pdf | 2025-07-03 21:00:00 |

</details>

---

<details>
  <summary>🙏 Acknowledgements</summary>

- [LangChain](https://www.langchain.com/)
- [Streamlit](https://streamlit.io/)
- [Groq](https://console.groq.com/)
- [Google Gemini](https://ai.google.dev/)
- [Chroma](https://docs.trychroma.com/)

</details>

---


Then return here for real-world patterns.

---

Happy building! 🛠️
