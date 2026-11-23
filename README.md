# LLM Playground Pro ⚡

> **An interactive educational studio for real streaming LLM API calls, token telemetry, quota tracking, and prompt engineering.**

LLM Playground Pro is a single-file, zero-build web app built with vanilla HTML, CSS, and modern JavaScript. It is designed to teach how Large Language Model APIs behave in production by connecting directly to inference providers (Groq by default, plus OpenAI, OpenRouter, and Cerebras) right from the browser.

Every control includes an educational helper note explaining what it does, what it costs, and how it impacts latency and quotas.

---

## 🎯 Key Educational Capabilities

1. **Live SSE Token Streaming & TTFT Latency:**
   - Measures true Time-To-First-Token (**TTFT**) from request initiation to the first non-reasoning content delta.
   - Shows real-time token throughput (tokens per second) and total wall-clock duration.
   - Toggle streaming off to feel the dramatic difference in perceived latency.

2. **Stateless Conversation Re-sending:**
   - Visualizes how chat history snowballs input token payload on every turn.
   - Includes a dynamic inline SVG chart tracking input token growth across turns.

3. **Rate Limit & Quota Gauge:**
   - Parses HTTP rate-limit response headers (`x-ratelimit-remaining-tokens`, `x-ratelimit-limit-tokens`, `x-ratelimit-remaining-requests`, `x-ratelimit-reset-tokens`).
   - Visualizes your remaining tokens-per-minute quota draining in real-time, shifting from green to amber and red.

4. **Deep Reasoning / Thinking Mode (CoT):**
   - Live stream tracking of hidden reasoning deltas (e.g., DeepSeek R1).
   - Dedicated collapsible thinking accordions showing that reasoning tokens count against your token budget and quota even when hidden.

5. **Prompt Analysis Engine:**
   - Classifies prompt structure into **ZERO-SHOT**, **ONE-SHOT**, or **FEW-SHOT** using multi-rule example detection.
   - Automatically detects Chain-of-Thought step-by-step cues, role instructions, output format constraints, and word limits.
   - Live token breakdown between system instructions, conversation history, and new prompt.

6. **Compare Mode & Variance Testing:**
   - **Compare Mode**: Run identical prompts side-by-side on two different setups (models, temperatures, seeds) simultaneously to benchmark TTFT, speed, tokens, and cost with automatic winner badges.
   - **Run 5x**: Execute 5 sequential runs to demonstrate statistical variance and token spread at temperatures greater than 0.

7. **Multi-Language Live Code Generator:**
   - Real-time generation of cURL, Python (`openai` client), JavaScript (`fetch`), and Node.js SDK snippets reflecting active parameters and message history.
   - Sanitized key handling using `$GROQ_API_KEY` environment variable placeholders.

8. **Safety & Zero-Leakage Privacy:**
   - **No backend, no analytics, no external trackers.**
   - API keys are held strictly in memory or `sessionStorage` (never in `localStorage`).
   - Keys are transmitted exclusively over encrypted TLS directly to the inference provider's API.

---

## 🚀 Deploy to Vercel (Zero Build Step)

You can deploy LLM Playground Pro to Vercel in seconds:

### Option A: Via GitHub (Recommended)
1. Push this folder to a GitHub repository:
   ```bash
   git init
   git add .
   git commit -m "feat: initial commit of LLM Playground Pro"
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   git push -u origin main
   ```
2. Open [Vercel Dashboard](https://vercel.com/new).
3. Import your GitHub repository.
4. Leave the Framework Preset as **Other** (no build command needed).
5. Click **Deploy**. Your app will be live with full HTTPS and Edge CDN caching!

### Option B: Via Vercel CLI
```bash
npm i -g vercel
cd "llm playground"
vercel
```

---

## 🔑 Supported Providers & API Keys

- **Groq (Default):** Free tier keys available at [console.groq.com/keys](https://console.groq.com/keys)
- **OpenAI:** Keys available at [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- **OpenRouter:** Keys available at [openrouter.ai/keys](https://openrouter.ai/keys)
- **Cerebras:** Ultra-fast inference keys at [cloud.cerebras.ai](https://cloud.cerebras.ai)

> **Note on Provider Parameters:** Model availability, token pricing, and supported parameters change over time. If a provider adjusts parameters, use the **Custom model ID** feature or check the respective provider documentation.

---

## ⌨️ Keyboard Shortcuts

- `Ctrl + Enter` / `Cmd + Enter`: Send prompt / Execute call
- `Escape`: Abort active stream (retains partial response)

---

## 📄 License
MIT License. Created for developers, educators, and AI practitioners.
