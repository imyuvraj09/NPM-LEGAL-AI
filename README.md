
<div align="center">

# ⚖️ NPM Legal AI

**Your AI-powered Legal Assistant — Upload documents, ask questions, get accurate answers.**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![LLaMA 3.2](https://img.shields.io/badge/LLaMA_3.2-0467DF?style=for-the-badge&logo=meta&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21F?style=for-the-badge&logo=huggingface&logoColor=black)
![RAG](https://img.shields.io/badge/RAG-8A2BE2?style=for-the-badge&logo=databricks&logoColor=white)
![MIT License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

*Built to make legal knowledge accessible to everyone.*

</div>

---

## What is NPM Legal AI?

**NPM Legal AI** is an intelligent legal document assistant that lets users upload **unlimited documents** (PDFs, images) and chat with them in natural language — with context-aware memory that persists across the entire conversation.

Built on **LLaMA 3.2** via a custom Hugging Face inference backend, it delivers **accurate, hallucination-resistant legal answers** by strictly grounding every response in the documents you provide.

> 💡 *No more sifting through 100-page legal contracts. Just ask.*

---

## Key Features

| Feature | Description |
|---|---|
| 📄 **Multi-document upload** | Upload PDFs and images into a named knowledge base — no document count limit |
| 🧠 **Persistent memory** | Session-scoped conversation history so follow-up questions always carry context |
| 🛡️ **Hallucination-resistant** | Instruction-tuned to refuse speculation — answers cite only what's in your documents |
| ⚡ **RAG pipeline** | Vector retrieval feeds only the relevant document chunks to LLaMA at query time |
| 🖥️ **Clean web UI** | Chat interface with file upload — no CLI required |
| ☁️ **HuggingFace backend** | Inference served from a Hugging Face Space — no local GPU needed |

---

## Architecture

```
Browser (HTML / CSS / JS)
        │  Chat UI, file upload, streaming responses
        ▼
Flask Web Server — app.py
        │  Routes · session memory (npmai.Memory) · HF API proxy
        ▼
HuggingFace Spaces — inference backend
        │  Document ingestion · vector knowledge base · LLaMA 3.2 (temp=0.5)
        ▼
LLaMA 3.2 generation
        Grounded, citation-only answers → streamed back to browser
```

---

## Quick Start

### Prerequisites

- Python 3.9+
- pip

### Installation

```bash
# Clone

git clone https://github.com/imyuvraj09/NPM-LEGAL-AI.git
cd NPM-LEGAL-AI/NPM-LEGAL-AI-main
# Install dependencies
pip install -r requirements.txt

# (Optional) set a secret key
export SECRET_KEY="your-secret-key-here"

# Run
python app.py
```

Open your browser and navigate to `(http://127.0.0.1:5000/)`.

---

## How to Use

```
1. 📂  Upload a PDF or image of your legal document
2. 🏷️  Give your knowledge base a name  (e.g. "lease-2024")
3. ❓  Type any question in plain language
4. 🤖  Get a grounded, document-only answer instantly
5. 💬  Continue the conversation — memory is retained throughout
```

> ⚠️ Only **one file source** (PDF or image) can be uploaded per query. Multiple queries can build on the same knowledge base.

---

## API Reference

| Key | Value |
|---|---|
| **Ingestion endpoint** | `https://yuvrajsingh22028704-npmeduai.hf.space/ingestion` |
| **Method** | `POST` (multipart/form-data) |
| **Secret key env var** | `SECRET_KEY` (defaults to dev key — change in production) |

---

## Project Structure

```
NPM-LEGAL-AI/
│
├── app.py                  # Flask routes, session memory, HF API calls
├── requirements.txt        # pip dependencies
├── LICENSE                 # MIT License
│
├── templates/
│   └── index.html          # Chat UI with file upload
│
└── static/
    └── NPMaistyle.css      # Styling with video background overlay
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Python · Flask · Gunicorn |
| **LLM** | LLaMA 3.2 via Hugging Face Spaces |
| **RAG / Memory** | `npmai` library · session-based context · vector DB |
| **Document ingestion** | PDF & image via multipart form |
| **Frontend** | HTML5 · CSS3 · Vanilla JavaScript |

### Dependencies

```txt
flask
requests
npmai
gunicorn
```

```bash
pip install -r requirements.txt
```

---

## Contributing

Contributions are welcome!

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "Add: your feature description"
git push origin feature/your-feature-name
# Open a Pull Request
```

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <i>Built with ❤️ for making legal knowledge accessible to everyone.</i>
</div>
