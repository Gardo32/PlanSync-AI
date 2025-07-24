<img src="assets/PlanSync-AI%20Logo.png" alt="PlanSync-AI Logo" width="80" style="float: left; margin-right: 12px;" />

# PlanSync-AI

**PlanSync-AI** is a fully autonomous Scrum Master platform built on [n8n](https://n8n.io). It automates agile workflows—sprint planning, task triage, and developer coordination—using AI and flexible workflow orchestration.

---

## 📦 Modules

PlanSync-AI is composed of modular components, each designed to automate key Scrum Master responsibilities.

| Module                                     | Purpose                                                                                                                                     | Status   |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| 🔥 [Sprint Spark](modules/Sprint-Spark.md) | Uses LLMs to analyze recent GitHub changes and automatically generate categorized Trello cards for bugs, features, and tech debt.           | ✅        |
| 🗣️ Standup Synth          | Replaces daily standups by summarizing GitHub activity and team progress into a digest, sent via Telegram or any webhook-compatible system. | 🛠️ In Progress    |
| 📅 **Ceremony Scheduler**                  | Auto-schedules sprint ceremonies with agenda, backlog links, and summaries using calendar, Trello, and GitHub integrations.                 | 🧪 Queue |
| 🚨 **Blocker Watchdog**                    | Detects `#blocker` tags across GitHub, Trello, or Slack and opens resolution tasks automatically while notifying stakeholders.              | 🧪 Queue |
| 🧹 **Backlog Auditor**                     | Continuously checks backlog stories for missing estimates, unclear descriptions, or poor formatting using LLMs, and flags or fixes them.    | 🧪 Queue |
| 📊 **Sprint Radar**                        | Monitors sprint health in real time, generating burndown charts, velocity graphs, and progress summaries daily.                             | 🧪 Queue |
| ⏳ **Retro Tracker**                        | Tracks retrospective action items across boards and alerts responsible members if deadlines are missed or work stalls.                      | 🧪 Queue |
| 📣 **Agile Whisperer**                     | Auto-posts Agile principles, reminders, and behavior nudges into Slack or Telegram based on team dynamics and metrics.                      | 🧪 Queue |

----

## 🚀 Features

* 🤖 **AI-powered sprint planning** via Gemini or ChatGPT
* 🔄 **Automatic GitHub diff triaging** into Trello (Bug / Feature / Technical Debt)
* 📬 **Smart Telegram notifications** with markdown-safe formatting
* 📂 **Git repo cloning** with intelligent file filtering
* 📉 **Burndown and velocity chart generation**
* 🧠 **Backlog quality enforcement using LLMs**
* 🧾 **Pluggable modules** for retrospectives, standups, and coaching

---

## 🧰 Tech Stack

### 🚀 MADE Stack
**Modern Applications with Docker & Events**

- **M** — Markup-first Frontend  
  _Next.js, React, Astro — build fast, render smart_

- **A** — Automation Layer  
  _n8n, Make, LangChain — orchestrate workflows and logic_

- **D** — Dockerized Deployment  
  _Containerization, scaling, and platform portability_

- **E** — Events via APIs & Webhooks  
  _Glue between services — trigger-driven, real-time communication_

**Tagline:**  
*“Build modern frontends, automate with APIs, connect everything through webhooks, and deploy anywhere — the MADE stack has you covered.”*

---

## 🤝 Contributing

We welcome contributions!
Fork the repo, build your own modules, or submit improvements — every PR helps improve PlanSync-AI.
Feel free to open issues for bugs, ideas, or feedback. 🚀
