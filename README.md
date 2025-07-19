<img src="assets/PlanSync-AI%20Logo.png" alt="PlanSync-AI Logo" width="80" style="float: left; margin-right: 12px;" />

# PlanSync-AI

**PlanSync-AI** is a fully autonomous Scrum Master platform built on [n8n](https://n8n.io). It automates agile workflows—sprint planning, task triage, and developer coordination—using AI and flexible workflow orchestration.

---

## 📦 Modules

PlanSync-AI is composed of modular components, each designed to automate key Scrum Master responsibilities.

| Module           | Purpose                                                                                                                                     | Status |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------|
| [Sprint Spark](modules/Sprint-Spark.md) | Uses LLMs to analyze recent GitHub changes and automatically generate categorized Trello cards for bugs, features, and tech debt. | ✅     |

---

## 🚀 Features

- 🤖 **AI-powered sprint planning** via Gemini or ChatGPT
- 🔄 **Automatic GitHub diff triaging** into Trello (Bug / Feature / Technical Debt)
- 📬 **Smart Telegram notifications** with markdown-safe formatting
- 📂 **Git repo cloning** with intelligent file filtering
- 🧪 **Language-aware prompting** (e.g., JS, Python, etc.)

---

## 🧰 Tech Stack

- [n8n](https://n8n.io) – Workflow automation engine  
- Google Gemini / LangChain – AI integration  
- GitHub API – Source control access  
- Trello API – Task board automation  
- Telegram API – Notifications  
- Bash, Node.js – Logic and scripting support  
