# 🗣️ Standup Synth

**Standup Synth** is a module of **PlanSync-AI** that automates daily standup meetings by analyzing team activity across GitHub repositories and generating intelligent progress summaries. It replaces traditional standup meetings with AI-powered digests sent via Telegram or webhooks.

---

## 🧠 What It Does

* Monitors GitHub activity across multiple repositories
* Analyzes commits, pull requests, and issues from the last 24 hours
* Identifies team member contributions and progress patterns
* Uses AI to generate meaningful standup summaries
* Detects blockers, completed work, and upcoming tasks
* Sends formatted digest reports via Telegram or webhook endpoints
* Tracks velocity and progress trends over time
* Provides actionable insights for team coordination

---

## 💡 How to Use

### Manual Trigger (Telegram)
Send a message to your connected Telegram bot:

```
/standup
```

Optional parameters:
```
/standup {team-name} {days}
```

* `team-name` — Filter by specific team or project (optional)
* `days` — Number of days to analyze (default: 1)

### Automated Schedule
The workflow can be configured to run automatically:
* Daily at 9:00 AM (configurable)
* Before scheduled team meetings
* On-demand via webhook triggers

---

## 🛠 Workflow Breakdown

Based on the actual n8n workflow implementation:

| Step                     | Description                                                | Node Type |
| ------------------------ | ---------------------------------------------------------- | --------- |
| Schedule Trigger         | Runs every weekday at 9:00 AM automatically               | Schedule Trigger |
| Variables Configuration  | Sets GitHub repos, team mapping, and notification settings | Code Node |
| GitHub Issues Fetcher    | Collects issues from the last 24 hours                    | GitHub API |
| GitHub PRs Fetcher       | Retrieves pull requests and reviews                       | GitHub API |
| GitHub Commits Fetcher   | Gets recent commits with detailed patch data               | GitHub API |
| Data Merger             | Combines all GitHub activity data                          | Merge Node |
| Activity Classifier     | Categorizes work: completed, in-progress, blocked         | Code Node |
| AI Summary Generator    | Uses Google Gemini to create standup summaries            | LangChain Agent |
| Format for Telegram     | Structures output with Markdown and emojis                | Code Node |
| Telegram Delivery      | Sends digest to configured team chat                       | Telegram Node |

### Key Features Implemented:
- **Parallel Data Fetching**: Multiple GitHub API calls run simultaneously
- **Smart Data Aggregation**: Intelligent merging and filtering of activities  
- **AI-Powered Summaries**: Google Gemini generates human-readable standups
- **Rich Formatting**: Telegram-optimized output with emojis and structure
- **Blocker Detection**: Automatic identification of impediments
- **Team Mapping**: GitHub usernames mapped to real names

---

## 📌 About the `Variables` Node

The `Variables` node configures team settings, repositories, and output formatting. You **must customize this node** with your team's configuration.

### ✅ Replace its code with this:

```js
return {
  // GitHub repository to monitor (format: "owner/repo")
  'Start variable': 'https://github.com/chartdb/chartdb {<number>limit: 100}',
  
  
  // Telegram configuration
  'telegram-chat-id': 'YOUR-TELEGRAM-CHAT-ID',
  
  // Time range settings (hours)
  'hours-back': 24,
  

};
```

### 🔁 Replace the placeholders:

* `'Start variable'`: GitHub repository URL with optional task limit
* `'team-members'`: Object mapping GitHub usernames to display names
* `'telegram-chat-id'`: Your Telegram chat ID for notifications
* `'hours-back'`: How many hours of activity to analyze (default: 24)
* `'repo-owner'` and `'repo-name'`: Repository details for GitHub API calls

These values configure the entire workflow for your team's specific setup.

---

## 🧾 Output Example

```markdown
# 📊 Daily Standup - March 15, 2024

## 🎯 Team Progress Summary
**Active Contributors:** 3 | **Commits:** 12 | **PRs:** 4 | **Issues Resolved:** 2

---

## 👥 Individual Updates

### John Doe (@john-dev)
**Yesterday:**
- ✅ Completed user authentication module (3 commits)
- ✅ Fixed mobile responsive issues in header component
- 🔄 Reviewed and merged PR #47 (API optimization)

**Today:**
- 🎯 Working on payment integration feature
- 🎯 Planning to start dashboard redesign

**Blockers:** None

---

### Jane Smith (@jane-frontend)
**Yesterday:**
- ✅ Updated UI components library (5 commits) 
- ✅ Implemented dark mode toggle functionality
- 🔄 Currently in PR review: #52 (Component refactoring)

**Today:**
- 🎯 Continue working on accessibility improvements
- 🎯 Code review for authentication module

**Blockers:** 🚨 Waiting for design approval on new color scheme

---

## 📈 Metrics & Insights
- **Velocity:** +15% compared to last week
- **PR Merge Rate:** 85% (4/5 PRs merged)
- **Average Commit Size:** 127 lines changed
- **Most Active Repo:** frontend-app (8 commits)

## 🚨 Action Items
- [ ] Jane needs design approval for color scheme
- [ ] Schedule API review meeting for next Monday
- [ ] Update testing documentation (overdue 2 days)

---
*Generated by PlanSync-AI Standup Synth at 09:00 UTC*
```

---

## 🤖 Prompt Template (LLM)

The LLM receives this structured instruction:

> Analyze the following GitHub activity data for our development team's daily standup report. 
>
> Create a comprehensive but concise summary that includes:
>
> 1. **Individual Updates**: For each team member, summarize:
>    - What they completed yesterday (✅)
>    - What they're working on today (🎯) 
>    - Any blockers or impediments (🚨)
>
> 2. **Team Metrics**: Calculate and highlight:
>    - Total commits, PRs, and issues resolved
>    - Velocity trends and productivity insights
>    - Repository activity distribution
>
> 3. **Action Items**: Identify:
>    - Potential blockers or dependencies
>    - Overdue tasks or stalled work
>    - Recommendations for team coordination
>
> Format the output in clean Markdown suitable for Telegram. Use emojis for visual clarity and keep individual updates concise but informative.
>
> Activity Data: `{github_activity_json}`
> Team Configuration: `{team_config}`
> Time Range: `{analysis_period}`

---

## ✅ Status

* ✅ **Complete** - Fully functional and tested
* GitHub activity analysis implemented
* Telegram integration working
* AI summary generation functional  
* Scheduled automation configured
* Webhook delivery ready
* Team member mapping operational
* Blocker detection active

---

## 🧭 Next Up

Planned improvements:

* **Calendar Integration**: Sync with team calendars and meeting schedules
* **Slack Support**: Additional notification channels beyond Telegram
* **Custom Templates**: Configurable standup formats for different teams
* **Historical Analytics**: Weekly/monthly progress reports and trends
* **Jira Integration**: Include ticket status and sprint progress
* **Smart Scheduling**: Adaptive timing based on team activity patterns
* **Blocker Escalation**: Automatic alerts for prolonged blockers

---

## 🔧 Configuration Tips

### Repository Setup
- Ensure the GitHub token has read access to all configured repositories
- Add repositories gradually to test the workflow before full deployment
- Consider repository grouping for large organizations

### Team Member Mapping
- Keep GitHub usernames and display names updated
- Include external contributors and contractors
- Set up fallback handling for unmapped users

### Notification Optimization
- Test different time zones and scheduling options
- Configure notification preferences per team member
- Set up backup notification channels

### AI Tuning
- Adjust prompt templates based on team feedback
- Fine-tune summary length and detail level
- Customize blocker detection keywords for your workflow

---

## 🔗 Back to [Main README](../README.md)
