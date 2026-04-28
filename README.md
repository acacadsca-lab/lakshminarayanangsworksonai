# AI Chat Project - Machine Learning Web Service

A comprehensive Django-based web application that integrates advanced AI/ML capabilities including conversational AI, audio processing, and text-to-speech functionality.

## 🎯 Project Overview

This is a production-ready machine learning web service built with Django, featuring:

- **AI-Powered Chat Interface** - Intelligent conversational AI with memory capabilities
- **Audio Processing** - Speaker recognition and audio analysis using pyannote.audio
- **Text-to-Speech (TTS)** - Multiple TTS engines including Qwen and custom voice synthesis
- **Vector Search** - FAISS-based semantic search for document retrieval
- **RAG Pipeline** - Retrieval-Augmented Generation using LangChain
- **Multi-Modal AI** - Integration with Hugging Face transformers and diffusers

## 📊 Technology Stack

### Backend
- **Framework**: Django 4.2.11
- **Server**: Gunicorn 21.2.0
- **Database**: PostgreSQL (via psycopg2-binary)
- **Deployment**: Heroku with WhiteNoise static file serving

### AI/ML Core
- **Deep Learning**: PyTorch 2.9.0
- **Transformers**: Hugging Face Transformers 4.40.2, Sentence Transformers 2.6.1
- **Diffusion Models**: Diffusers 0.27.2
- **Vector DB**: FAISS (Facebook AI Similarity Search)

### Audio & Speech
- **Audio Processing**: Librosa 0.10.1
- **Speaker Diarization**: Pyannote.audio 3.1.1
- **Text-to-Speech**: Qwen TTS with fallback options

### Language Model Framework
- **LangChain**: LangChain 0.1.20, LangChain Core 0.1.52
- **Community Integrations**: LangChain Community 0.0.38
- **Document Processing**: PyPDF 2, PyPDF2 3.0.1

### Frontend
- **HTML**: 66.8% of codebase
- **CSS**: 7.1% of codebase
- **JavaScript**: 2.3% of codebase
- **Backend Rendering**: Django Templates

## 🏗️ Project Structure

```
.
├── aichatprojectfinal/          # Main Django project directory
│   ├── aichatprojectfinal/      # Project configuration
│   ├── chatapp/                 # Main Django application
│   │   ├── models.py            # Database models for chats, messages, embeddings
│   │   ├── views.py             # Request handlers and business logic
│   │   ├── urls.py              # URL routing
│   │   ├── forms.py             # Django forms
│   │   ├── custom_gpt.py        # Custom AI engine implementation
│   │   ├── tts_processor.py     # Text-to-speech processing
│   │   ├── tts_voice.py         # Voice synthesis
│   │   ├── utils.py             # Utility functions
│   │   ├── static/              # CSS, JavaScript, images
│   │   ├── templates/           # HTML templates
│   │   └── migrations/          # Database migrations
│   ├── faiss_20/                # FAISS vector store for semantic search
│   ├── memorybot/               # Long-term memory management
│   ├── manage.py                # Django management script
│   ├── settings.py              # Django configuration
│   ├── wsgi.py                  # WSGI application entry point
│   └── requirements.txt          # Python dependencies
├── qwen3.py                     # Qwen model integration
├── qwen_audio.py                # Qwen audio processing
├── QWENTTS.py                   # Qwen TTS implementation
├── backup.py                    # Backup utilities
├── setup_tts_env.sh             # TTS environment setup script
├── runtime.txt                  # Python runtime version for Heroku
└── requirements.txt             # Root-level dependencies

```

## 🚀 Getting Started

### Prerequisites
- Python 3.x
- PostgreSQL (or SQLite for development)
- FFmpeg (for audio processing)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/acacadsca-lab/lakshminarayanangsworksonai.git
   cd lakshminarayanangsworksonai
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the project root:
   ```
   DEBUG=False
   SECRET_KEY=your-secret-key-here
   DATABASE_URL=postgresql://user:password@localhost/dbname
   ALLOWED_HOSTS=localhost,127.0.0.1
   ```

5. **Run migrations**
   ```bash
   cd aichatprojectfinal
   python manage.py migrate
   ```

6. **Start the development server**
   ```bash
   python manage.py runserver
   ```

   The application will be available at `http://localhost:8000`

### TTS Setup

To enable text-to-speech functionality:

```bash
bash setup_tts_env.sh
pip install -r requirements_tts.txt
```

## 📋 Key Features

### 1. **Intelligent Chat Interface**
- Powered by custom GPT implementation
- Conversation history and context management
- Multi-turn dialogue support

### 2. **Semantic Search**
- FAISS-based vector similarity search
- Document embeddings using Sentence Transformers
- RAG (Retrieval-Augmented Generation) pipeline

### 3. **Audio Capabilities**
- Speaker diarization (identifying who spoke when)
- Audio feature extraction
- Real-time audio processing

### 4. **Text-to-Speech**
- Multiple TTS engines (Qwen, fallback options)
- Voice synthesis and customization
- Audio file generation and streaming

### 5. **Document Processing**
- PDF parsing and processing
- Text extraction and chunking
- Vector embedding for semantic search

## 🔧 Configuration

### Django Settings
Edit `aichatprojectfinal/settings.py` to configure:
- Database connections
- Static files and media
- Installed apps
- Middleware
- Authentication

### Model Configuration
- Transformer model selection
- FAISS index parameters
- TTS model selection

## 📦 Dependencies Management

**Core ML Libraries:**
- PyTorch: Deep learning framework
- Transformers: Pre-trained language models
- Sentence-Transformers: Semantic embeddings

**Data Processing:**
- Librosa: Audio analysis
- PyPDF2: PDF processing

**Web Framework:**
- Django: Web framework
- Gunicorn: WSGI server

See `requirements.txt` for complete list and versions.

## 🌐 Deployment

The project is configured for Heroku deployment:

1. **Configure Heroku environment**
   ```bash
   heroku login
   heroku create your-app-name
   ```

2. **Set environment variables**
   ```bash
   heroku config:set DATABASE_URL=postgresql://...
   heroku config:set SECRET_KEY=your-secret-key
   ```

3. **Deploy**
   ```bash
   git push heroku main
   ```

4. **Run migrations on Heroku**
   ```bash
   heroku run python aichatprojectfinal/manage.py migrate
   ```

## 📚 Usage Examples

### Starting a Chat Session
```python
# Via Django shell
python manage.py shell
from chatapp.models import Chat
chat = Chat.objects.create(title="My Conversation")
```

### Using the Custom GPT
```python
from chatapp.custom_gpt import CustomGPT
gpt = CustomGPT()
response = gpt.generate_response("Your query here")
```

### Text-to-Speech
```python
from chatapp.tts_voice import TextToSpeech
tts = TextToSpeech()
audio = tts.synthesize("Hello, world!")
```

## 🧪 Testing

Run tests with:
```bash
cd aichatprojectfinal
python manage.py test
```

## 📝 API Endpoints

The application provides various API endpoints through Django URLs. Check `aichatprojectfinal/chatapp/urls.py` for the complete routing configuration.

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋 Support & Questions

For issues, questions, or suggestions, please open an [Issue](https://github.com/acacadsca-lab/lakshminarayanangsworksonai/issues) on GitHub.

## 📞 Contact

**Project Owner**: [acacadsca-lab](https://github.com/acacadsca-lab)

---

**Last Updated**: 2026-04-28 13:29:06

**Repository**: [acacadsca-lab/lakshminarayanangsworksonai](https://github.com/acacadsca-lab/lakshminarayanangsworksonai)
