# 🏛️ SmartScheme AI

**Voice-First Multilingual Government Scheme Assistant**

## Problem Statement

Millions of Indian citizens—especially senior citizens, farmers, and rural communities—struggle to access and understand government welfare schemes due to:
- **Language barriers** (schemes documented in English/complex language)
- **Digital literacy gaps** (complex forms and interfaces)
- **Information overload** (uncertainty about eligibility)
- **Accessibility challenges** (no voice-based interaction for benefits discovery)
- **Low adoption** of digital government services

**SmartScheme AI** solves this by providing a voice-first, conversational AI assistant that helps citizens discover, understand, and apply for government schemes in their own language.

## Features

- 🗣️ **Voice Interaction** — Speak in English, Telugu, or Hindi; system responds in the same language
- 🔍 **AI Scheme Discovery** — Answer a few questions to find schemes you're eligible for
- 💬 **Conversational Assistant** — Ask questions naturally about any government scheme
- ✅ **Eligibility Checker** — Check if you're eligible for specific schemes with detailed reasoning
- 📄 **PDF Summarizer** — Upload scheme PDFs and get instant summaries in your language
- 🔊 **Listen Aloud** — Every response can be read aloud in your preferred language
- 🌐 **Multilingual** — Full support for English, Telugu (తెలుగు), and Hindi (हिन्दी)

## Tech Stack

### Frontend & UI
- **Streamlit** — Rapid web application framework for data apps

### AI & LLM
- **Ollama** — Local LLM inference (llama3, qwen3, gemma3)
- **OpenAI** — GPT-based models (bring your own key)
- **Google Gemini** — Gemini API integration (bring your own key)

### Natural Language Processing
- **sentence-transformers** — Multilingual embeddings for semantic search
- **faster-whisper** — Speech-to-text transcription (multilingual)
- **edge-tts** — Text-to-speech synthesis

### Data & Retrieval
- **ChromaDB** — Vector database for scheme embeddings and retrieval
- **PyMuPDF** — PDF document processing and extraction

### Localization & Languages
- **Custom i18n System** — JSON-based translations (English, Hindi, Telugu)
- **Language Support** — English, Hindi (हिन्दी), Telugu (తెలుగు)

### Core Libraries
- **Python 3.x** — Backend runtime
- **pandas** — Data processing
- **requests** — HTTP client for API calls

## Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the Application

```bash
streamlit run app.py
```

The app opens at `http://localhost:8501`.

## Configuration

### AI Provider Setup

#### Option A: Ollama (Local - Recommended)

1. Install [Ollama](https://ollama.com)
2. Pull a model:
   ```bash
   ollama pull llama3
   ollama pull qwen3
   ollama pull gemma3
   ```
3. Ensure Ollama is running (default: `http://localhost:11434`)
4. Open Settings (⚙️) in the app → Select Ollama → Set endpoint and model

#### Option B: OpenAI (BYOK)

1. Get an API key from [OpenAI](https://platform.openai.com)
2. Open Settings → Select OpenAI → Enter your API key

#### Option C: Gemini (BYOK)

1. Get an API key from [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Open Settings → Select Gemini → Enter your API key

### Language Settings

Open Settings (⚙️) → Select your preferred language:
- English
- తెలుగు (Telugu)
- हिन्दी (Hindi)

## Project Structure

```
SmartScheme-AI/
├── app.py                  # Main entry point
├── pages/
│   ├── home.py             # Landing page
│   ├── discover.py         # Scheme discovery form
│   ├── chat.py             # Conversational assistant
│   ├── eligibility.py      # Eligibility checker
│   ├── pdf_summary.py      # PDF upload & summarization
│   └── settings.py         # AI provider & language settings
├── ai/
│   ├── base_provider.py    # Abstract base class
│   ├── provider_router.py  # Provider factory & routing
│   ├── ollama_provider.py  # Ollama integration
│   ├── openai_provider.py  # OpenAI integration
│   └── gemini_provider.py  # Gemini integration
├── voice/
│   ├── speech_to_text.py   # Whisper-based STT
│   └── text_to_speech.py   # Edge-TTS based TTS
├── rag/
│   ├── vectorstore.py      # ChromaDB vector store
│   ├── ingest.py           # Document ingestion
│   └── retrieve.py         # Semantic retrieval
├── translations/
│   ├── en.json             # English translations
│   ├── te.json             # Telugu translations
│   └── hi.json             # Hindi translations
├── utils/
│   ├── i18n.py             # Internationalization manager
│   ├── localization.py     # Localization helpers
│   ├── scheme_engine.py    # Recommendation & eligibility engine
│   ├── conversation.py     # Conversation manager
│   └── helpers.py          # Utility functions
├── data/
│   └── schemes/
│       └── schemes.json    # 25+ government schemes dataset
├── requirements.txt
├── .env.example
└── README.md
```

## Usage

### Citizen Mode (Default)

The app opens in citizen-friendly mode with large buttons and simple navigation:

1. **Home** — Overview with quick voice access
2. **Discover Schemes** — Fill in your details to find matching schemes
3. **Chat Assistant** — Ask questions in your language
4. **Eligibility Checker** — Check eligibility for specific schemes
5. **PDF Summary** — Upload scheme PDFs for instant analysis

### Advanced Settings

Click ⚙️ Settings in the navigation to access:
- Language switching
- AI provider configuration
- Voice settings

## Architecture

### AI Provider Router Pattern

```
User → Provider Router → OllamaProvider / OpenAIProvider / GeminiProvider
                         → Unified response format
```

### RAG Pipeline

```
Documents → DocumentIngester → ChromaDB (vector store)
Query → Retriever → Semantic Search → Context → AI Response
```

### Voice Pipeline

```
Microphone → faster-whisper (STT) → Text → AI → Response Text → edge-tts (TTS) → Speaker
```

## Requirements

- Python 3.10+
- 4GB+ RAM (8GB recommended for local AI)
- Microphone (for voice features)
- Internet connection (for cloud AI providers)

## License

MIT
