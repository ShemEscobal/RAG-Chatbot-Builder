# RAG Chatbot Builder 🤖

A modern, no-code web platform for creating intelligent RAG (Retrieval-Augmented Generation) chatbots using your own documents. Build powerful AI assistants without writing a single line of code!

## ✨ Features

### 🎨 Intuitive User Interface
- **Modern, responsive design** with Tailwind CSS
- **Drag-and-drop document upload**
- **Real-time chat testing**
- **Easy configuration** - no coding required

### 🧠 Powerful RAG Capabilities
- **Multiple LLM providers**: OpenAI (GPT-3.5, GPT-4), Anthropic (Claude)
- **Vector stores**: ChromaDB, FAISS
- **Document support**: PDF, TXT, DOCX, CSV
- **Customizable parameters**: temperature, chunk size, retrieval settings
- **Source citations** in responses

### 🔧 Built With
- **Frontend**: React + TypeScript + Vite + Tailwind CSS
- **Backend**: Python + FastAPI + LangChain
- **Vector Stores**: ChromaDB, FAISS
- **Document Processing**: PyPDF, python-docx, pandas

## 🚀 Quick Start

### Prerequisites

- **Python 3.9+**
- **Node.js 18+**
- **OpenAI API Key** (required for OpenAI models)

### Backend Setup

1. **Navigate to backend directory**
```bash
cd backend
```

2. **Create virtual environment**
```bash
python -m venv venv
```

3. **Activate virtual environment**

Windows:
```powershell
.\venv\Scripts\Activate.ps1
```

Linux/Mac:
```bash
source venv/bin/activate
```

4. **Install dependencies**
```bash
pip install -r requirements.txt
```

5. **Configure environment variables**

Create a `.env` file in the `backend` directory:
```env
OPENAI_API_KEY=your_openai_api_key_here
ANTHROPIC_API_KEY=your_anthropic_api_key_here  # Optional
```

6. **Run the backend server**
```bash
python main.py
```

The API will be available at `http://localhost:8000`

### Frontend Setup

1. **Navigate to frontend directory**
```bash
cd frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Run the development server**
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## 📖 Usage Guide

### Creating Your First Chatbot

1. **Open the application** in your browser (`http://localhost:5173`)

2. **Click "New Chatbot"** button

3. **Configure your chatbot**:
   - Enter a name and description
   - Choose LLM provider (OpenAI/Anthropic)
   - Select model (GPT-3.5, GPT-4, Claude, etc.)
   - Adjust temperature and other parameters
   - Add optional system prompt

4. **Save configuration**

5. **Upload documents**:
   - Drag & drop files or click to browse
   - Supported formats: PDF, TXT, DOCX, CSV
   - Wait for processing to complete

6. **Test your chatbot**:
   - Click "Chat" to open the chat interface
   - Ask questions about your documents
   - Get AI-powered responses with source citations

### Configuration Options

#### LLM Settings
- **Provider**: OpenAI or Anthropic
- **Model**: Choose from available models
- **Temperature**: Control randomness (0-2)
  - Lower = more focused and deterministic
  - Higher = more creative and diverse
- **Max Tokens**: Limit response length

#### RAG Settings
- **Vector Store**: ChromaDB (persistent) or FAISS (fast)
- **Chunk Size**: Document splitting size (100-4000)
- **Chunk Overlap**: Overlap between chunks (0-1000)
# RAG Chatbot Builder 🤖

A modern, no-code web platform for creating Retrieval-Augmented Generation (RAG) chatbots from your own documents. Upload PDFs, DOCX, TXT, or CSV files and let the assistant answer questions with source citations.

## Highlights
- Drag-and-drop document upload and ingestion
- Multiple LLM providers (OpenAI, Anthropic, Groq, Ollama)
- Embedding options: Ollama (local), HuggingFace (local/model hub), OpenAI
- Persistent vector stores (ChromaDB) and FAISS support
- Rich chat UI with Markdown-rendered responses (tables supported)
- Upload progress indicator and printable chat view

## Quick Start

Prerequisites
- Python 3.9+
- Node.js 18+

Backend (FastAPI)
1. Open a terminal and change into the backend directory:

```powershell
cd backend
```

2. Create and activate a virtual environment (example uses PowerShell on Windows):

```powershell
python -m venv .venv
& .\.venv\Scripts\Activate.ps1
```

3. Install Python dependencies:

```powershell
pip install -r requirements.txt
```

4. Create a `.env` file in `backend/` and add any provider keys you need:

```env
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key  # optional
GROQ_API_KEY=your_groq_api_key            # optional (for Groq provider)
```

5. Run the backend:

```powershell
python -m uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`.

Frontend (React + Vite)
1. Open a second terminal and change into the frontend directory:

```bash
cd frontend
```

2. Install dependencies and run the dev server:

```bash
npm install
npm run dev
```

The web UI will run at `http://localhost:5173` (or the port reported by Vite).

## Usage Notes

- Create a new chatbot, configure the LLM provider and model, then upload documents.
- Supported file types: `PDF`, `TXT`, `DOCX`, `CSV`.
- Document ingestion performs splitting, embedding, and indexing into the configured vector store.
- In the Chat UI assistant messages are rendered from Markdown (via `marked`) with sanitization (DOMPurify), so tables render correctly.
- Upload progress shows a spinner and a visual progress bar. Server-side processing progress (embedding/indexing) is not streamed to the UI by default.
 - The ChatbotBuilder UI includes a `Retrieval K` numeric control so users can adjust how many chunks are retrieved per query (default: 4). Change it in the chatbot configuration before saving to tune retrieval behavior.

### Key Configuration Options

- `chunk_size` and `chunk_overlap`: control how documents are split for embeddings.
- `retrieval_k`: number of top chunks retrieved for each query (default: `4` in the UI). Tune between 2–8 depending on your documents and model.
- `embedding_provider`: choose `ollama_gpu`, `ollama_cpu`, `huggingface`, or `openai`.

### Groq Models
The frontend includes a Groq model option `openai/gpt-oss-120b` (select provider = Groq, then choose this model in the dropdown).

## Project Structure

```
RAG/
├── backend/                # FastAPI backend, LangChain integration
│   ├── main.py
│   ├── services/rag_service.py
│   ├── models/
│   └── data/               # chatbots, vector stores, uploads
└── frontend/               # React + TypeScript app
    ├── src/
    │   ├── api/chatbot.ts
    │   ├── pages/ChatbotBuilder.tsx
    │   └── pages/ChatInterface.tsx
    └── package.json
```

## API (selected endpoints)

- `POST /api/chatbots` — create a chatbot
- `GET /api/chatbots` — list chatbots
- `POST /api/chatbots/{id}/documents` — upload documents
- `GET /api/chatbots/{id}/documents` — list documents
- `POST /api/chatbots/{id}/chat` — chat with the bot

## Troubleshooting & Tips

- If uploads fail or backend crashes when using Ollama embeddings, try `huggingface` embeddings or `ollama_cpu` mode (more stable).
- Windows file locks: deleting a chatbot that uses Chroma may fail if the process still holds file handles. Restarting the backend releases locks.
- If Markdown tables aren't rendering in chat bubbles, ensure the frontend bundle is up-to-date (hard refresh) — assistant messages use sanitized HTML.

## Development Notes & Future Work

- Server-side ingestion progress (SSE/polling) is not yet implemented — the UI reports HTTP upload progress only.
- Consider adding a small registry of opened vector-store instances so `delete_chatbot` can reliably close handles before deleting files.

## Contributing

Contributions welcome — open issues or PRs. Be sure not to commit secrets (API keys) to source control.

---

Built with ❤️ using Python, FastAPI, React, and LangChain
