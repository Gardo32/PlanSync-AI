# 🚨 Blocker Watchdog

**Blocker Watchdog** is a module of **PlanSync-AI** that continuously monitors for blockers across GitHub, Trello, and Slack, automatically detecting impediments and initiating resolution workflows. It helps Scrum Masters proactively identify and resolve team blockers before they impact sprint velocity.

---

## 🧠 What It Does

* Monitors GitHub issues, pull requests, and comments for blocker indicators
* Scans Trello cards for blocker labels and keywords in descriptions
* Watches Slack channels for blocker-related messages and mentions
* Detects blocker patterns using AI analysis of team communications
* Automatically creates resolution tasks and assigns appropriate stakeholders
* Sends escalation notifications to Scrum Masters and team leads
* Tracks blocker resolution time and generates impediment reports
* Provides dashboard insights on team velocity impact

---

## 💡 How to Use

### Automatic Detection
The workflow monitors continuously for blocker keywords and patterns:
- GitHub: `blocked`, `blocker`, `stuck`, `waiting for`, `dependency`
- Trello: Cards labeled with blocker tags or containing impediment keywords
- Slack: Messages with blocker mentions, help requests, and escalation patterns

### Manual Escalation
Team members can trigger immediate blocker processing:
```
@blocker-bot escalate [issue-link]
```

### Supported Blocker Types
- **Technical Blockers**: API dependencies, infrastructure issues, code conflicts
- **Resource Blockers**: Waiting for design, approval, external teams
- **Process Blockers**: Missing requirements, unclear specifications
- **External Blockers**: Third-party services, vendor dependencies

---

## 🛠 Workflow Design (Planned Implementation)

| Step                     | Description                                                | Integration |
| ------------------------ | ---------------------------------------------------------- | ----------- |
| Multi-Channel Monitor   | Continuous monitoring across GitHub, Trello, and Slack    | Webhooks + Polling |
| AI Pattern Recognition  | Identifies blocker language and context patterns          | LLM Analysis |
| Blocker Classification  | Categories blockers by type, severity, and impact         | ML Classification |
| Stakeholder Assignment  | Maps blockers to appropriate resolution owners             | Team Mapping |
| Resolution Task Creation| Creates action items in project management tools          | API Integration |
| Escalation Engine       | Sends notifications based on blocker age and severity     | Multi-Channel |
| Progress Tracking       | Monitors resolution status and time-to-resolution         | Data Analytics |
| Impact Reporting        | Generates velocity and impediment trend reports           | Dashboard API |

### Key Features (Planned):
- **Smart Detection**: AI-powered blocker identification beyond simple keywords
- **Automated Workflows**: Self-healing processes for common blocker types
- **Escalation Ladders**: Automatic escalation based on blocker age and impact
- **Cross-Platform**: Unified blocker management across all team tools
- **Analytics**: Blocker trend analysis and velocity impact measurement

---

## 📌 Configuration (Design Specification)

### Blocker Keywords Configuration
```js
return {
  blockerKeywords: {
    high_priority: ['blocked', 'blocker', 'critical dependency'],
    medium_priority: ['stuck', 'waiting for', 'needs approval'],
    low_priority: ['question', 'unclear', 'help needed']
  },
  
  escalationRules: {
    immediate: ['critical', 'production down', 'security'],
    urgent: 2, // hours before escalation
    standard: 24, // hours before escalation
    low: 72 // hours before escalation
  },
  
  stakeholderMapping: {
    'technical': ['tech-lead', 'senior-dev'],
    'design': ['design-lead', 'ux-team'],
    'product': ['product-owner', 'business-analyst'],
    'external': ['scrum-master', 'project-manager']
  },
  
  notificationChannels: {
    slack: {
      immediate: '#critical-alerts',
      escalated: '#team-blockers',
      resolved: '#standup-updates'
    },
    telegram: {
      scrum_master: 'SCRUM-MASTER-CHAT-ID',
      tech_leads: 'TECH-LEADS-GROUP-ID'
    }
  }
};
```

---

## 🧾 Expected Output Example

```markdown
# 🚨 BLOCKER ALERT - HIGH PRIORITY

**Blocker ID:** BLK-2024-0127-001
**Source:** GitHub Issue #456
**Status:** Active (2.5 hours)
**Impact:** Sprint Goal at Risk

## 📋 Blocker Details
**Title:** API authentication service down - blocking user login
**Type:** Technical Dependency
**Severity:** Critical
**Reporter:** @jane-dev
**Detected:** 2024-01-27 14:30 UTC

## 🎯 Assignment
**Primary Owner:** @tech-lead-mike
**Secondary:** @senior-dev-alex
**Scrum Master:** @sarah-sm (notified)

## 📊 Impact Analysis
- **Affected Stories:** 3 user stories (8 story points)
- **Team Members Blocked:** 2 developers
- **Sprint Risk:** HIGH - Core functionality unavailable

## 🚀 Suggested Actions
1. **Immediate:** Contact infrastructure team for service status
2. **Backup Plan:** Implement temporary authentication bypass for development
3. **Communication:** Update stakeholders on timeline impact

## ⏱️ SLA Status
- **Time Active:** 2h 30m
- **Escalation Level:** 1 of 3
- **Next Escalation:** In 30 minutes (3-hour SLA)

---
*Auto-generated by PlanSync-AI Blocker Watchdog*
```

---

## 🤖 AI Detection Prompts (Planned)

### Blocker Classification Prompt
> Analyze the following team communication for potential blockers or impediments:
>
> **Classification Goals:**
> 1. Identify if this represents a genuine blocker or just a question
> 2. Determine blocker type: Technical, Resource, Process, or External
> 3. Assess severity: Critical, High, Medium, Low
> 4. Estimate impact on team velocity and sprint goals
> 5. Suggest appropriate stakeholders for resolution
>
> **Context:** `{communication_data}`
> **Team Info:** `{team_mapping}`
> **Current Sprint:** `{sprint_context}`

### Resolution Tracking Prompt
> Monitor the following blocker for resolution indicators:
>
> **Tracking Goals:**
> 1. Detect resolution signals in follow-up communications
> 2. Identify if blocker is being actively addressed
> 3. Flag if blocker requires escalation or additional resources
> 4. Measure time-to-resolution for reporting
>
> **Blocker Data:** `{blocker_context}`
> **Recent Activity:** `{activity_data}`

---

## ⚙️ Implementation Roadmap

### Phase 1: Foundation (Current)
- [ ] Design workflow architecture
- [ ] Define blocker detection patterns
- [ ] Create escalation rule engine
- [ ] Build stakeholder mapping system

### Phase 2: Core Detection
- [ ] Implement GitHub issue/PR monitoring
- [ ] Add Trello card scanning capabilities
- [ ] Integrate Slack message analysis
- [ ] Deploy AI classification system

### Phase 3: Automation
- [ ] Automated task creation workflows
- [ ] Multi-channel notification system
- [ ] Escalation ladder implementation
- [ ] Resolution tracking automation

### Phase 4: Analytics
- [ ] Blocker trend analysis dashboard
- [ ] Velocity impact reporting
- [ ] Team impediment insights
- [ ] Continuous improvement recommendations

---

## ✅ Status

* 🧪 **In Design** - Architecture and requirements phase
* Core detection patterns identified
* Stakeholder mapping strategies defined
* Integration points with existing modules planned
* **Next**: Begin Phase 1 implementation

---

## 🧭 Next Steps

### Immediate Priorities:
1. **Workflow Architecture**: Design n8n workflow structure for multi-source monitoring
2. **Detection Engine**: Implement AI-powered blocker classification system
3. **Integration Layer**: Connect with existing Sprint Spark and Issue Tracker Gateway
4. **Notification System**: Build multi-channel alert and escalation system

### Future Enhancements:
- **Predictive Analytics**: Machine learning for blocker prediction
- **Auto-Resolution**: Automated workflows for common blocker types
- **Mobile Alerts**: Push notifications for critical blockers
- **Integration Hub**: Connect with Jira, Azure DevOps, and other tools
- **Custom Workflows**: Team-specific blocker resolution processes

---

## 🔧 Design Considerations

### Performance Requirements
- Real-time processing for critical blockers (< 5 minutes)
- Scalable monitoring across multiple repositories and channels
- Efficient AI processing to minimize false positives

### Security & Privacy
- Secure handling of sensitive project information
- Role-based access to blocker details and resolution actions
- Audit trail for all blocker detection and resolution activities

### Team Adoption
- Non-intrusive monitoring that doesn't disrupt team workflows
- Clear escalation paths that respect team autonomy
- Configurable sensitivity levels for different team preferences

---

## 🔗 Back to [Main README](../README.md)
