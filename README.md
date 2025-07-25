<img src="assets/PlanSync-AI%20Logo.png" alt="PlanSync-AI Logo" width="80" style="float: left; margin-right: 12px;" />

# PlanSync-AI

**PlanSync-AI** is a collection of standalone n8n workflows that automate Scrum Master responsibilities. Each module is designed to work independently until the next development phase introduces an AI agent to aggregate and coordinate all workflows.

> 🚀 **Coming Next**: Integration with **PlaySync Pages** - a drag-n-drop frontend application for creating easy dashboards and interfaces for n8n and any automation service using webhooks.

---

## � Project Structure

### `/standalone/` - Independent Workflow Modules
Ready-to-use n8n workflows that can be imported and run immediately. Each workflow is completely self-contained and doesn't depend on other modules.

**Available Workflows:**
- `Sprint Spark.json` - Automated sprint planning and GitHub diff triage
- `Standup Synth.json` - Daily standup automation and progress summaries

See [`standalone/README.md`](standalone/README.md) for detailed setup instructions.

### `/modules/` - Documentation & Guides
Detailed documentation for each workflow module, including setup guides, configuration options, and usage examples.

---

## 🔄 Development Phases

### Phase 1: Standalone Workflows ✅ (Current)
- Individual n8n workflows that work independently
- Each module solves a specific Scrum Master task
- Easy to import, configure, and use
- No dependencies between modules

### Phase 2: AI Agent Integration 🔄 (Next)
- AI agent to aggregate and coordinate all standalone workflows
- Unified configuration and monitoring
- Cross-module communication and data sharing
- Intelligent workflow orchestration

### Phase 3: PlaySync Pages Integration 🎯 (Future)
- Integration with **PlaySync Pages** drag-n-drop frontend
- Visual dashboard creation for automation workflows
- Easy webhook management and monitoring
- User-friendly interface for non-technical team members

---

## �📦 Standalone Modules

PlanSync-AI is composed of standalone workflow modules, each designed to automate specific Scrum Master responsibilities. **All modules are currently independent and can be used separately without dependencies.**

| Module                                     | Purpose                                                                                                                                     | Status   | Workflow File |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------------- |
| 🔥 [Sprint Spark](modules/Sprint-Spark.md) | Uses LLMs to analyze recent GitHub changes and automatically generate categorized Trello cards for bugs, features, and tech debt.           | ✅        | `standalone/Sprint Spark.json` |
| 🗣️ [Standup Synth](modules/Standup-Synth.md) | Replaces daily standups by summarizing GitHub activity and team progress into a digest, sent via Telegram or any webhook-compatible system. | ✅        | `standalone/Standup Synth.json` |
| ⚡ Issue Tracker Gateway               | Transforms GitHub issues into organized Trello cards with automated labeling, milestone tracking, and progress visualization.              | 🛠️ In Progress | TBD |
| 🧹 **Backlog Auditor**                     | Continuously checks backlog stories for missing estimates, unclear descriptions, or poor formatting using LLMs, and flags or fixes them.    | 🧪 Queue | TBD |
| 📊 **Sprint Radar**                        | Monitors sprint health in real time, generating burndown charts, velocity graphs, and progress summaries daily.                             | 🧪 Queue | TBD |
| ⏳ **Retro Tracker**                        | Tracks retrospective action items across boards and alerts responsible members if deadlines are missed or work stalls.                      | 🧪 Queue | TBD |
| 📅 **Ceremony Scheduler**                  | Auto-schedules sprint ceremonies with agenda, backlog links, and summaries using calendar, Trello, and GitHub integrations.                 | 🧪 Queue | TBD | 

> **Note**: Until the AI agent integration phase, each module operates independently. You can import and use any workflow without setting up others.

## 🚀 Quick Start

1. **Choose a workflow**: Browse the [`standalone/`](standalone/) directory for available n8n workflows
2. **Import to n8n**: Open your n8n instance and import the desired `.json` file
3. **Configure**: Set up required API keys and connections (see [`standalone/README.md`](standalone/README.md))
4. **Run**: Activate the workflow and enjoy automated Scrum Master assistance!

Each workflow is designed to work independently - no need to set up the entire platform.

---

## 🚀 Features

* 🤖 **Standalone n8n workflows** - Import and run individual automation modules
* 🔄 **Independent operation** - Each module works without dependencies on others
* 🎯 **GitHub diff triaging** - Automatic categorization into Trello (Bug/Feature/Tech Debt)
* 📬 **Smart notifications** - Telegram and webhook integrations with markdown formatting
* 📂 **Git repository analysis** - Intelligent file filtering and change detection
* 🧠 **AI-powered insights** - LLM integration for intelligent task categorization
* 🔌 **Plug-and-play modules** - Easy to customize and extend individual workflows
* 🎨 **Future-ready** - Designed for integration with PlaySync Pages drag-n-drop frontend

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

We welcome contributions to individual workflows and the overall project!

### Contributing to Standalone Workflows:
- Fork the repo and modify individual workflow JSON files
- Test your changes in your n8n instance
- Submit PRs with workflow improvements or new modules
- Share configurations and customizations

### Future Contributions:
- Help build the AI agent aggregation system
- Contribute to PlaySync Pages frontend integration
- Improve documentation and setup guides

Feel free to open issues for bugs, ideas, or feedback. Every contribution helps make automation more accessible! 🚀
