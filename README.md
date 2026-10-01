# EduGenie - AI Learning Assistant & Personal Tutor

EduGenie is a modern, responsive AI-powered learning assistant built with Python 3.10+, FastAPI, and the Gemini API (with optional local LaMini-Flan-T5 model support).

---

## 🌟 Key Features

1. **Student Q&A Assistant** (`/api/qa`): Ask complex homework or study questions and get clear AI answers.
2. **Beginner Concept Explainer** (`/api/explain`): Simplifies complex topics using analogies, core breakdowns, and real-world examples. Supports Gemini API or optional local LaMini-Flan-T5 model with automatic fallback.
3. **Interactive 3-Question Quiz Generator** (`/api/quiz`): Generates exactly 3 multiple-choice questions with 4 options each, interactive answer selection, instant scoring, and explanations.
4. **Concise Text Summarizer** (`/api/summarize`): Summarizes study text into short, medium, or detailed key points with word count reduction statistics.
5. **Beginner-to-Advanced Learning Path** (`/api/learning-path`): Generates a structured sequential roadmap of learning modules with key takeaways and action steps.

---

## 🚀 Setup & Installation Guide (Windows PowerShell)

Follow these steps to set up and run EduGenie locally on Windows PowerShell.

### Step 1: Open PowerShell and Navigate to Workspace
```powershell
Set-Location -Path "d:\naan mudhalvan 2 year\Edugenie -AI\Edugenie"
```

### Step 2: Create and Activate Virtual Environment
```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### Step 3: Install Required Dependencies
```powershell
pip install -r requirements.txt
```

*(Optional: If you wish to use the local LaMini-Flan-T5 model for explanations, install PyTorch and Transformers):*
```powershell
pip install transformers torch
```

### Step 4: Configure Environment Variables (`.env`)
Copy `.env.example` to `.env` if you haven't already:
```powershell
Copy-Item .env.example .env
```
Open `.env` in your text editor and add your Gemini API Key:
```env
GEMINI_API_KEY=your_actual_gemini_api_key_here
GEMINI_MODEL=gemini-2.5-flash
ENABLE_LOCAL_MODEL=false
HOST=127.0.0.1
PORT=8000
```
> 🔑 **Note on Model Name**: You can easily change `GEMINI_MODEL` in `.env` to `gemini-3.7-flash` or `gemini-2.5-pro` depending on your Google AI Studio access.

### Step 5: Start the Server with Uvicorn
Run the exact Uvicorn command:
```powershell
uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

---

## 🌐 Application Endpoints

- **Web UI**: Open your browser at [http://127.0.0.1:8000](http://127.0.0.1:8000)
- **Health Check**: [http://127.0.0.1:8000/health](http://127.0.0.1:8000/health)
- **Interactive OpenAPI Docs**: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

---

## 🛡️ Error Handling & Reliability

- **HTTP 429 Quota/Rate Limits**: Displays user-friendly warning banners advising when to retry without making redundant API calls.
- **API Key & Network Validation**: Clear diagnostic logging on the server without exposing secrets, and informative UI messages.
- **Double-Click Prevention**: Submit buttons are disabled and show a loading spinner during API requests.
- **Local Model Fallback**: If local model loading fails due to missing dependencies or OOM, EduGenie gracefully falls back to Gemini API.
