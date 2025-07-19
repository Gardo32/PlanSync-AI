# 🧠 PlanSync-AI

**PlanSync-AI** is an intelligent Scrum Master automation platform powered by [n8n](https://n8n.io). It simplifies agile team management by automating sprint planning, task triaging, and developer coordination using AI and workflow automation.

---

## 📦 Modules

PlanSync-AI is composed of modular components, each designed to automate a specific responsibility typically handled by a Scrum Master.

| Module         | Purpose                                                                 | Status |
|----------------|-------------------------------------------------------------------------|--------|
| [Sprint Spark](modules/Sprint-Spark.md) | Automates sprint planning by analyzing recent code changes and generating Trello cards for bugs, features, and tech debt using LLMs. | ✅ |

---

## 🚀 Features

- 🤖 AI-assisted sprint planning using Gemini / ChatGPT
- 🔄 Auto-triaging GitHub diffs into Trello cards (Bug / Feature / Technical Debt)
- 📬 Smart Telegram notifications with markdown-safe messages
- 📂 Git repo cloning and filtered file analysis
- 🧪 Code-type-aware AI prompting (JS, Python, etc.)

---

## 🧰 Tech Stack

- [n8n](https://n8n.io) (workflow engine)
- Google Gemini / LangChain LLMs
- GitHub API (source control)
- Trello API (task board)
- Telegram API (notifications)
- Bash, Node.js (command and code nodes)

