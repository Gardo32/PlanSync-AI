# Standalone Workflows

This directory contains standalone n8n workflow files that can be imported and run independently. Each workflow is a complete, self-contained automation module for specific Scrum Master tasks.

## 📋 Available Workflows

### 🔥 Sprint Spark (`Sprint Spark.json`)
**Purpose**: Automated sprint planning and task triage
- Analyzes recent GitHub changes using AI
- Automatically generates categorized Trello cards (Bug/Feature/Tech Debt)
- Integrates with GitHub, Trello, and LLM services
- **Status**: ✅ Complete and tested

### 🗣️ Standup Synth (`Standup Synth.json`)
**Purpose**: Automated daily standup summaries
- Summarizes GitHub activity and team progress
- Generates digest reports sent via Telegram
- Scheduled to run automatically every weekday at 9 AM
- **Status**: ✅ Complete and tested

## 🚀 How to Use

1. **Import to n8n**: Open your n8n instance and import the desired `.json` workflow file
2. **Configure credentials**: Set up required API keys and connections (GitHub, Trello, Telegram, etc.)
3. **Customize settings**: Adjust parameters like repository URLs, board IDs, notification channels
4. **Activate workflow**: Enable the workflow to start automation

## 🔧 Requirements

Each workflow requires specific integrations and credentials:

### Common Requirements:
- n8n instance (self-hosted or cloud)
- GitHub API access
- LLM API key (OpenAI, Google Gemini, etc.)

### Sprint Spark Specific:
- Trello API credentials
- Repository access permissions

### Standup Synth Specific:
- Telegram Bot API (or webhook endpoint)
- Team member configuration

## 🏗️ Future Integration

These standalone workflows are designed to be:
- **Independent**: Each can run without dependencies on others
- **Modular**: Easy to customize and extend
- **Integration-ready**: Will be aggregated by an AI agent in the next development phase

## Next Steps
The next phase will introduce an AI agent that:
1. Aggregates all standalone workflows
2. Coordinates between modules
3. Provides unified configuration and monitoring
4. Integrates with **PlaySync Pages** - a drag-n-drop frontend for creating dashboards and interfaces for n8n and automation services

## 🤝 Contributing

Each workflow is self-contained and can be improved independently:
- Fork and modify individual workflows
- Add new standalone modules
- Share configurations and customizations
- Report issues or suggest enhancements

For questions or support, open an issue in the main repository.
