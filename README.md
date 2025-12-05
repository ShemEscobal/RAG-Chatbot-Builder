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
- **Retrieval K**: Number of relevant chunks to retrieve (1-20)

#### Advanced
- **System Prompt**: Custom instructions for the AI

## 🏗️ Project Structure

```
RAG/
├── backend/
│   ├── main.py                 # FastAPI application
│   ├── config.py               # Configuration settings
│   ├── requirements.txt        # Python dependencies
│   ├── models/
│   │   └── chatbot.py         # Pydantic models
│   ├── services/
│   │   └── rag_service.py     # RAG logic and LangChain integration
│   └── data/                   # Data storage (auto-created)
│       ├── chatbots/          # Chatbot configurations
│       └── uploads/           # Uploaded documents
│
└── frontend/
    ├── src/
    │   ├── App.tsx            # Main React component
    │   ├── main.tsx           # Entry point
    │   ├── index.css          # Global styles
    │   ├── api/
    │   │   └── chatbot.ts     # API client
    │   ├── components/
    │   │   └── Layout.tsx     # Layout component
    │   └── pages/
    │       ├── Dashboard.tsx       # Chatbot list
    │       ├── ChatbotBuilder.tsx  # Chatbot configuration
    │       └── ChatInterface.tsx   # Chat UI
    ├── package.json
    ├── vite.config.ts
    ├── tailwind.config.js
    └── tsconfig.json
```

## 🔌 API Endpoints

### Chatbots
- `POST /api/chatbots` - Create chatbot
- `GET /api/chatbots` - List all chatbots
- `GET /api/chatbots/{id}` - Get chatbot details
- `PUT /api/chatbots/{id}` - Update chatbot
- `DELETE /api/chatbots/{id}` - Delete chatbot

### Documents
- `POST /api/chatbots/{id}/documents` - Upload documents
- `GET /api/chatbots/{id}/documents` - List documents
- `DELETE /api/chatbots/{id}/documents/{doc_id}` - Delete document

### Chat
- `POST /api/chatbots/{id}/chat` - Send chat message

## 🛠️ Tech Stack Details

### Backend
- **FastAPI**: Modern, fast web framework
- **LangChain**: LLM orchestration framework
- **ChromaDB**: Vector database for embeddings
- **FAISS**: Fast similarity search
- **Pydantic**: Data validation
- **OpenAI/Anthropic SDKs**: LLM integration

### Frontend
- **React 18**: UI library
- **TypeScript**: Type safety
- **Vite**: Fast build tool
- **Tailwind CSS**: Utility-first styling
- **React Router**: Navigation
- **Axios**: HTTP client
- **React Dropzone**: File uploads
- **React Markdown**: Markdown rendering
- **Lucide React**: Beautiful icons

## 🔐 Security Notes

- **Never commit your `.env` file** with API keys
- Keep your API keys secure
- Consider rate limiting for production use
- Implement user authentication for multi-user scenarios

## 🚧 Future Enhancements

- [ ] Streaming responses
- [ ] Multiple conversation threads
- [ ] Export/import chatbot configurations
- [ ] Chat history persistence
- [ ] More LLM providers (local models, Ollama, etc.)
- [ ] Advanced RAG techniques (HyDE, multi-query, etc.)
- [ ] User authentication and multi-tenancy
- [ ] Analytics and usage tracking
- [ ] Chatbot embedding (iframe/widget)

## 📝 License

MIT License - feel free to use this project for your own applications!

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## 💡 Tips

1. **Start with smaller documents** to test your chatbot
2. **Adjust chunk size** based on document type:
   - Technical docs: 500-1000
   - General text: 1000-2000
3. **Lower temperature (0.3-0.5)** for factual responses
4. **Higher temperature (0.7-0.9)** for creative responses
5. **Review sources** to understand where answers come from

## ❓ Troubleshooting

### Backend won't start
- Verify Python version: `python --version` (3.9+)
- Check virtual environment is activated
- Ensure all dependencies installed: `pip install -r requirements.txt`
- Verify `.env` file exists with valid API key

### Frontend won't start
- Verify Node version: `node --version` (18+)
- Delete `node_modules` and reinstall: `npm install`
- Check console for error messages

### Upload fails
- Verify file format is supported
- Check file size (default max: 10MB)
- Ensure backend is running

### Chat not working
- Verify documents are uploaded
- Check API key is valid
- Look at browser console and backend logs

## 📧 Support

For issues or questions, please open a GitHub issue.

---

**Built with ❤️ using Python, React, and LangChain**
