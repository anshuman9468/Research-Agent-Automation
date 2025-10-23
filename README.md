# Research-Agent-Automation
This is the Research Automation Agent Made in n8n workflow. I made this to make the research more easy and fast and should be secure and give the fast results.# 🧠 Research Agent — n8n Workflow

## 🌍 Overview
This project is a **no-code AI Research Agent** built in using **LangChain nodes**.  
It allows users to **ask research-based questions** in chat, and the agent intelligently uses **Perplexity AI** as an integrated tool to fetch and summarize accurate information — all orchestrated visually without any manual coding.

---

## ⚙️ Key Features
- 💬 **Chat-triggered research automation** — starts when a message is received  
- 🧩 **LangChain agent integration** for reasoning and tool calling  
- 🤖 **OpenAI GPT-4.1-mini** as the main LLM  
- 🔍 **Perplexity AI tool** (`sonar-deep-research` model) for deep factual queries  
- 🧱 **100% no-code workflow** — built entirely within n8n’s visual editor  
- 🪄 **Dynamic query handling** — intelligently routes questions to the best source  

---

## 🗂️ Files
- `Research_agent.json` → Exported n8n workflow file (import directly into n8n)

---

## 🧩 Node Architecture

| Node | Type | Purpose |
|------|------|----------|
| **When Chat Message Received** | `@n8n/n8n-nodes-langchain.chatTrigger` | Triggers the workflow when a new chat message arrives |
| **AI Agent** | `@n8n/n8n-nodes-langchain.agent` | Central orchestrator using LangChain Agent logic |
| **OpenAI Chat Model** | `@n8n/n8n-nodes-langchain.lmChatOpenAi` | Provides LLM reasoning and response generation |
| **Message a Model in Perplexity** | `n8n-nodes-base.perplexityTool` | Fetches real-time web and research-based data |

---

## ⚙️ Setup Instructions

### 1️⃣ Import the Workflow
1. Open your **n8n dashboard**.  
2. Go to **Workflows → Import from File**.  
3. Upload the `Research_agent.json` file.

---

### 2️⃣ Add Credentials
- **OpenAI Credentials:**  
  Add your OpenAI API key under *Credentials → OpenAI API* (the workflow currently uses GPT-4.1-mini).  
- **Perplexity Credentials:**  
  Add your Perplexity API key under *Credentials → Perplexity API* (used by the sonar-deep-research model).

---

### 3️⃣ Configure Nodes
1. **When Chat Message Received:**  
   - Acts as the entry trigger. You can test by executing manually or connecting to your chat endpoint.

2. **AI Agent Node:**  
   - Contains the system message:  
     > “You are a helpful assistant. Use the Perplexity tool to give me the answers to my asked questions.”
   - This ensures that when a question is asked, the agent automatically decides when to invoke the Perplexity tool.

3. **OpenAI Chat Model:**  
   - Model: `gpt-4.1-mini`  
   - Handles reasoning, contextual replies, and message construction.

4. **Perplexity Tool:**  
   - Model: `sonar-deep-research`  
   - Executes web-based factual research and returns summarized results to the AI Agent.

---

### 4️⃣ Test the Workflow
- Click **Execute Workflow**.  
- In the chat input, ask a research-oriented question such as:  
  > “Summarize the latest advancements in quantum computing.”  
- The agent will use **Perplexity** to find reliable information and then generate a concise answer using **GPT-4.1-mini**.

---

### 5️⃣ Extend or Customize
- Replace GPT-4.1-mini with another OpenAI model (like `gpt-4-turbo`).  
- Add more tools (e.g., Wikipedia, Wolfram, or Google Search) for broader research.  
- Integrate a chat UI or Telegram/Discord bot for real-time interaction.

---

## 🧠 Learning Outcomes
Through this workflow, I learned:
- How to connect **multiple AI models** and **tools** in a single no-code automation  
- How to build **LangChain-style reasoning agents** in n8n  
- How to integrate **Perplexity API** for real-time research tasks  
- How to create reusable **no-code AI automation templates**

---

## 👨‍💻 Author
**Anshuman Dutta**  

---

## ⚠️ Notes
- Use the workflow responsibly and avoid overloading external APIs.  
- Ensure your API keys are kept private and not shared in public repositories.  
- The Perplexity tool requires an active API plan.


