# Bender Enterprise v6.1 - Local RAG UI

Bender Enterprise is a lightweight, high-performance web interface designed for **Local RAG (Retrieval-Augmented Generation)**. It allows you to chat with local LLMs via Ollama while providing the ability to upload documents for context-aware responses—all running 100% locally in your browser.

![Bender Interface](https://img.icons8.com/color/96/futurama-bender.png)

## 🚀 Key Features

* **Multi-Format RAG Support**: Upload and "shred" documents to use as context. Supported formats: `.pdf`, `.docx`, `.xlsx`, `.xls`, `.txt`, `.csv`.
* **Multiple Chats Management**: Create, rename, and switch between different conversation threads.
* **Smart Message Handling**:
    * **Dynamic Controls**: Messages cannot be sent unless text is typed.
    * **Delete Individual Messages**: Remove specific user queries or AI responses to fine-tune the conversation history.
    * **Copy Chat History**: Export the entire conversation to your clipboard with one click.
    * **Context Window**: Automatically remembers the last **10 messages** to maintain coherent dialogue.
* **Visual & UX Enhancements**:
    * **Light/Dark Mode**: Smooth theme transitions saved to your browser preferences.
    * **Generation State**: UI intelligently locks (Sidebar and New Chat) while Bender is thinking to prevent state conflicts.
    * **Bender Quotes**: Randomized witty greetings upon startup.
* **Privacy & Storage**: Everything is stored in your browser's `localStorage`. No data ever leaves your machine (except to your local Ollama instance).

## 🛠 Configuration

You can easily customize the behavior in the JavaScript section of the file. Here is the default configuration:

```javascript
const CONFIG = {
    OLLAMA_URL: 'http://localhost:11434/api/chat', 
    MODEL_NAME: 'llama3.1:8b',
    CONTEXT_WINDOW: 10,
    SYSTEM_PROMPT_DEFAULT: "You are Bender, a helpful robot assistant. Be precise and witty.",
    SYSTEM_PROMPT_DOCS: "You are Bender. FOCUS STRICTLY ON THE PROVIDED DOCUMENTS.",
    QUOTES: [
        "System ready. What are we solving today, meatbag?",
        "I'm faster than a vending machine coffee, and likely smarter.",
        "I'm here to do the thinking so you don't have to.",
        "Local LLM at your service. Just ask!",
        "I'm bored. Give me a complicated PDF to shred."
    ]
};
```

## 📂 Document Handling & Constraints

* **Multiple Uploads**: You can attach several documents to a single chat session.
* **Storage Note**: Extracted text is stored in `localStorage`. 
* **Recommended Limit**: To ensure smooth browser performance and stay within standard browser storage quotas, it is recommended to keep the total combined text content under **5MB**.

## 🏁 Quick Start

For the best and lowest-latency experience, **it is highly recommended to run Ollama on the same machine** as this UI.

**1. Start Ollama**
Ensure Ollama is running. If you encounter CORS issues, set the environment variable:
`export OLLAMA_ORIGINS="*"` and restart Ollama.

**2. Run the Web Server**
Bender is a zero-dependency frontend. Run it using a simple one-liner:

**Linux / macOS / Windows (with Python):**
```bash
python3 -m http.server 8000
```
Then open your browser at `http://localhost:8000`.

---
*Created with wit and metal. "Bite my shiny metal interface!"*
