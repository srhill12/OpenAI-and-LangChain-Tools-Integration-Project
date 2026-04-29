# Generative AI Agent System — OpenAI + LangChain Tools Integration

A generative AI project demonstrating the design and deployment of 
LLM-powered agents using OpenAI's GPT-3.5-turbo and LangChain's tools 
framework — capable of reasoning across multiple external data sources 
to answer complex, multi-step queries.

---

## Business Context

Enterprise AI adoption is increasingly moving beyond single-model 
completions toward agentic systems — AI that can reason, select tools, 
call external APIs, and chain actions together to complete multi-step 
tasks. This project demonstrates the core architecture pattern behind 
that shift: an LLM agent that decides which tool to use, executes it, 
interprets the result, and continues reasoning until the task is complete.

This capability is directly relevant to enterprise Gen AI deployment 
contexts where organizations need AI systems that can integrate with 
existing data sources, APIs, and workflows rather than operating in 
isolation.

---

## What It Does

Implements a LangChain agent powered by GPT-3.5-turbo with four 
integrated tools:

- **Wikipedia Tool** — retrieves and synthesizes factual information 
  from Wikipedia in response to knowledge queries
- **OpenWeatherMap Tool** — queries real-time weather data via API 
  based on natural language location references
- **Calculator Tool** — performs mathematical computations as part of 
  multi-step reasoning chains
- **Custom Tool** — demonstrates extending the agent with 
  organization-specific capabilities beyond built-in tools

### Example Queries the Agent Handles

- *"What is the age of the mayor of the capital of Canada?"* — requires 
  Wikipedia lookup + reasoning about current age
- *"What is the current weather in the city where penicillin was first 
  isolated?"* — requires Wikipedia lookup for location, then weather API 
  call
- *"What is a fun fact about the sum of 22 and 35?"* — requires 
  calculation followed by knowledge retrieval

---

## Technical Architecture

User Query
↓
LangChain Agent (GPT-3.5-turbo)
↓ reasons about which tool to use
Tool Selection & Execution
├── Wikipedia API
├── OpenWeatherMap API
├── Calculator
└── Custom Tool
↓
Result Interpretation
↓
Final Response

**Key design pattern:** The agent decides autonomously which tools to 
invoke and in what order — the user does not need to specify a workflow. 
This is the foundation of enterprise agentic AI systems.

---

## Setup

```bash
git clone https://github.com/srhill12/OpenAI-and-LangChain-Tools-Integration-Project.git
cd OpenAI-and-LangChain-Tools-Integration-Project
python -m venv env
source env/bin/activate
pip install -r requirements.txt
```

Create a `.env` file in the project root:

OPENAI_API_KEY=your_openai_api_key
OPENWEATHER_API_KEY=your_openweather_api_key

---

## Governance & Responsible Deployment Notes

Agentic AI systems introduce governance challenges that single-model 
systems do not — because agents take actions, not just generate text.

**Scope Control**  
This agent is scoped to four specific tools. In a production deployment, 
tool selection must be deliberately limited — an agent with unrestricted 
tool access (including write actions) poses significant risk. Scope 
restriction is a primary governance control for agentic systems.

**Action Reversibility**  
All tools in this implementation are read-only — the agent retrieves 
information but cannot modify data, send messages, or execute 
transactions. This is an intentional design constraint. Any agentic 
system with write capabilities requires additional human oversight 
controls and confirmation workflows before actions are taken.

**Transparency & Auditability**  
LangChain's agent framework exposes the reasoning chain — which tools 
were called, with what inputs, and what was returned. This auditability 
is essential for governance: you cannot govern what you cannot observe. 
In a production deployment, this reasoning trace should be logged and 
retained for review.

**Prompt Injection Risk**  
Agents that retrieve content from external sources (Wikipedia, APIs, 
web pages) are vulnerable to prompt injection — malicious content in 
retrieved data that attempts to redirect the agent's behavior. This is 
an active area of AI security research and a governance consideration 
for any production agentic deployment.

**Human Oversight**  
For high-stakes tasks (financial decisions, communications sent on 
behalf of users, data modifications), agentic systems should require 
explicit human confirmation before executing consequential actions. 
This project's read-only design reflects that principle.

---

## Connection to Enterprise Gen AI Deployment

The patterns demonstrated here — tool integration, multi-step reasoning, 
external API orchestration, scope restriction — are the same patterns 
that underpin enterprise Gen AI systems at scale. The governance 
principles applied (scope control, read-only constraints, auditability, 
injection awareness) translate directly to production deployment 
requirements for responsible agentic AI.

---

## Possible Enhancements

- Expand toolset with domain-specific APIs (financial data, legal 
  databases, internal knowledge bases)
- Add a Streamlit or Gradio interface for non-technical users
- Implement logging of agent reasoning chains for audit purposes
- Add input/output guardrails to prevent prompt injection
- Build confirmation workflows for any write-capable tool extensions

---

## Origin

This project was developed as part of the Ohio State University 
AI & ML Bootcamp (2024) and expanded with enterprise governance 
framing for portfolio purposes.

---

## Author

**Steven Hill**  
AI Ethics & Policy Professional | Purdue University MSAI  
[LinkedIn](https://linkedin.com/in/stevenrhill) | 
[GitHub](https://github.com/srhill12)