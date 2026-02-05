# Gemini Flash Chat (Flask + React)

A minimal full-stack chat application built with **Flask (Python)** on the backend and **React (via CDN)** on the frontend.  
It connects to **Google Gemini** models and exposes a simple chat UI in the browser.

This project is intended as a **starter template / experiment**, not a production-ready system.

---

## Project Structure

.
├── main1.py # Flask backend

└── templates/

└── index.html # React + Tailwind frontend (CDN-based)


---

## Features

- Flask backend with a single `/chat` API endpoint
- Google Gemini model integration
- React 18 frontend (no build step, runs directly in the browser)
- Tailwind CSS via CDN
- Simple settings modal to configure backend API URL
- Streaming-style chat UX (non-streaming backend)

---

## Tech Stack

**Backend**
- Python 3
- Flask
- Google Gemini SDK (`google.genai`)

**Frontend**
- React 18 (UMD)
- Tailwind CSS (CDN)
- Babel (in-browser JSX compilation)

---

## Backend (`main1.py`)

The backend exposes:
- `GET /` → serves the frontend
- `POST /chat` → forwards user input to Gemini and returns raw text output

Key implementation details:
- No authentication
- No rate limiting
- No request validation
- API key is currently **hardcoded** (⚠️ bad practice)

Source: :contentReference[oaicite:0]{index=0}

---

## Frontend (`index.html`)

The frontend is a single-page React app embedded directly in HTML:
- Uses `fetch()` to call the `/chat` endpoint
- Handles loading, errors, and connection failures
- Stores API endpoint URL in `localStorage`

There is **no bundler, no build step, and no SSR**.

Source: :contentReference[oaicite:1]{index=1}

---

## Setup & Run

### 1. Install dependencies
```bash
pip install flask google-genai

2. Set your Gemini API key (RECOMMENDED)

Replace the hardcoded key with an environment variable:

export GEMINI_API_KEY="your_api_key_here"


Then update main1.py accordingly.

3. Run the server
python main1.py

4. Open in browser
http://localhost:5001

Known Issues & Limitations

Be aware of these before pushing this anywhere serious:

❌ API key is hardcoded (security risk)

❌ No input sanitization

❌ No error handling around Gemini API failures

❌ No conversation memory (stateless requests)

❌ No deployment config (Docker, WSGI, etc.)

❌ Not suitable for production as-is

Why This Exists

This project is useful if you want:

A fast Gemini playground

A no-build React frontend

A learning example for Flask + LLM APIs

If your goal is scalable chat, analytics, or “data analysis,” this needs significant refactoring.
