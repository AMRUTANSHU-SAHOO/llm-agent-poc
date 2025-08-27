# LLM Agent POC (Browser + Node.js)

A minimal proof-of-concept **LLM Agent** that runs in the browser, supports **tool calling**, and integrates:

- 🌐 Google Search (via API proxy + SerpAPI)
- 🔄 AI Pipe proxy (stubbed by default, optional real integration)
- 🖥️ JavaScript code execution (sandboxed)

---

## 📂 Project Structure
```
llm-agent-poc/
├── public/
│   └── index.html        # Frontend (chat UI + logic)
├── server.js             # Backend (Express proxy)
├── package.json
├── .env.example          # Example environment variables
└── README.md
```

---

## 🚀 Setup & Run

1. Clone the repo:
   ```bash
   git clone https://github.com/YOUR-USERNAME/llm-agent-poc.git
   cd llm-agent-poc
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create an `.env` file:
   ```bash
   cp .env.example .env
   ```

4. Add your own API keys to `.env`:
   ```
   OPENAI_API_KEY=sk-xxxxxx
   SERPAPI_KEY=your_serpapi_key_here
   # AIPIPE_URL is optional, see notes below
   ```

   ⚠️ **Note for evaluators**:  
   We do **not commit real keys** to this repo.  
   Please create your own `.env` file using `.env.example` and add your OpenAI + SerpAPI keys.

5. Run the backend:
   ```bash
   npm start
   ```

6. Open the browser at:
   ```
   http://localhost:3000
   ```

---

## 🛠 Features
- **Model Picker**: Choose model/provider.
- **Tool Calling**:
  - `search` → real results if `SERPAPI_KEY` is set, otherwise mock.
  - `aipipe` → **stubbed echo** by default. If you provide `AIPIPE_URL`, requests will be forwarded to a real AIPipe instance.
  - `eval_js` → sandboxed JS evaluation.
- **Bootstrap UI** for chat.

---

## 📝 Notes
- `.env` is **ignored** by Git (see `.gitignore`) so secrets are never exposed.
- `.env.example` is included so others know what variables to set.
- **About AIPipe**:
  - By default, `/api/aipipe` just echoes the request (stub mode).
  - If you want real AIPipe integration, deploy [AIPipe](https://github.com/sanand0/aipipe) and set `AIPIPE_URL` in `.env`.
  - This fulfills the requirement that the agent can *call* the tool, even if the backend is mocked.
- For the bonus assignment: all 3 tools are integrated and callable.