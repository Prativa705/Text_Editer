# 🚀 Smart Text Editor – AI-Powered Autocorrect & Suggestions

A modern, browser-based **smart text editor** that provides **real-time autocorrect** and **word suggestions** using the **Ollama AI API** with the `gemma2:2b` model.

## ✨ Features
- 📝 **Real-time autocorrect** for individual words as you type.
- 💡 **Next-word suggestions** based on your current sentence.
- 🎨 Clean, responsive **UI with gradient backgrounds**.
- 📊 **Word & character counter**.
- ⚡ **Instant feedback** with success/error status messages.
- 🔗 Easy integration with **Ollama AI** running locally.

---

## 📦 Tech Stack
- **Frontend:** HTML5, CSS3, JavaScript (Vanilla)
- **Backend AI:** [Ollama](https://ollama.com) running locally
- **Model:** `gemma2:2b`

---

## 🚀 Getting Started

### 1️⃣ Install Ollama
Download and install Ollama on your machine:

**For macOS/Linux:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
````

**For Windows (via WSL/Docker):**
Follow the official guide: [https://ollama.com/download](https://ollama.com/download)

---

### 2️⃣ Start Ollama Service

Ollama runs a local server on port `11434` by default.

Check if it's running:

```bash
ollama --version
```

If it's not running, start it:

```bash
ollama serve
```

> ⚠️ If you see "Only one usage of each socket address", Ollama is already running in the background. No need to restart.

---

### 3️⃣ Pull the Gemma2:2b Model

```bash
ollama pull gemma2:2b
```

---

### 4️⃣ Clone This Repository

```bash
git clone https://github.com/yourusername/smart-text-editor.git
cd smart-text-editor
```

---

### 5️⃣ Open in Browser

Simply open `index.html` in your browser.

Make sure Ollama is running, then start typing in the editor and press **space** to see autocorrect and suggestions.

---

## ⚙️ How It Works

1. The JavaScript frontend listens for **space key events**.
2. On detecting a new word or phrase, it sends an **API request** to:

   * `/api/chat` (Ollama local API) with the `gemma2:2b` model.
3. The AI responds with:

   * **Autocorrected word** (if needed)
   * **Next-word suggestion**
4. The UI displays buttons to apply changes instantly.

---

## 📁 Project Structure

```
smart-text-editor/
│
├── index.html      # Main HTML structure & script
├── style.css       # Inline styles in HTML
├── README.md       # Project documentation
└── screenshot.png  # Optional preview image
```

---

## 🔧 API Endpoints Used

* **`POST /api/chat`** → For multi-turn messages (autocorrect & suggestions).
* **Model:** `gemma2:2b`
* **Temperature:** `0` (deterministic output)

Example request:

```json
{
  "model": "gemma2:2b",
  "messages": [
    {
      "role": "user",
      "content": "Act as autocorrect expert..."
    }
  ],
  "stream": false,
  "temperature": 0
}
```

---

## 🛠 Troubleshooting

* **CORS errors?**

  * You need to enable CORS or serve `index.html` via a local server:

    ```bash
    python -m http.server 8000
    ```

    Then open: `http://localhost:8000`

* **Ollama not responding?**

  * Ensure `ollama serve` is running.
  * Check port availability with:

    ```bash
    netstat -ano | findstr 11434
    ```


## 🙌 Acknowledgements

* [Ollama](https://ollama.com) for the local AI server
* Google’s [Gemma2](https://ai.google/discover/gemma/) model
 

