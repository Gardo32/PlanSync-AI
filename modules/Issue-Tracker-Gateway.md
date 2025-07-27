# 🎯 Issue Tracker Gateway

**Issue Tracker Gateway** is a module of **PlanSync-AI** that automatically bridges GitHub issues with Trello project management. It listens for new GitHub issues via webhooks and instantly creates corresponding Trello cards with AI-enhanced descriptions and proper categorization.

---

## 🧠 What It Does

* Monitors GitHub repositories for new issue creation via webhooks
* Captures complete issue data including title, body, labels, and metadata
* Uses AI to analyze and enhance issue descriptions for better clarity
* Automatically creates Trello cards with structured information
* Maps GitHub labels to appropriate Trello labels and categories
* Includes direct links back to the original GitHub issue
* Provides real-time synchronization between development and project management

---

## 💡 How to Use

### Automatic Webhook Trigger
The workflow activates automatically when:
- A new issue is created in the configured GitHub repository
- GitHub sends a webhook payload to the n8n workflow
- No manual intervention required once set up

### Supported Events
Currently configured for:
- **Issue Creation**: New issues automatically trigger Trello card creation
- Future support planned for issue updates, comments, and closures

---

## 🛠 Workflow Breakdown

Based on the actual n8n workflow implementation:

| Step                     | Description                                                | Node Type |
| ------------------------ | ---------------------------------------------------------- | --------- |
| GitHub Trigger          | Listens for GitHub issue webhooks from repository         | GitHub Webhook |
| Data Aggregation        | Processes and formats the GitHub issue payload            | Code Node |
| AI Analysis Chain       | Analyzes issue content and generates Trello card data     | LangChain LLM |
| Structured Parser       | Ensures valid JSON output with proper formatting          | Output Parser |
| Variables Merger        | Injects Trello list ID and configuration settings         | Code Node |
| Trello Card Creator     | Creates the final card in the specified Trello board      | Trello API |

### Key Features Implemented:
- **Real-time Webhook Processing**: Instant response to GitHub events
- **AI-Enhanced Descriptions**: Google Gemini improves issue clarity
- **Structured Data Output**: JSON schema validation for consistency
- **Error Handling**: Retry logic and format correction
- **Configurable Mapping**: Customizable Trello list and label assignments

---

## 📌 About the `Merge Variables` Node

The `Merge Variables` node configures where Trello cards will be created. You **must customize this node** with your actual Trello board configuration.

### ✅ Replace its code with this:

```js
const LIST_ID = 'YOUR-TRELLO-LIST-ID';

for (const item of items) {
  if (item.json.output && Array.isArray(item.json.output)) {
    item.json.output = item.json.output.map(obj => {
      return {
        ...obj,
        listID: LIST_ID,
      };
    });
  }
}

return items;
```

### 🔁 Replace the placeholders:

* `YOUR-TRELLO-LIST-ID`: The ID of the Trello list where new issue cards should be created
* Configure the GitHub repository settings in the GitHub Trigger node
* Set up your Trello API credentials for card creation

These values determine where GitHub issues will appear in your Trello workflow.

---

## 🧾 Output Example

When a GitHub issue is created, the AI generates a Trello card like this:

```json
[
  {
    "name": "Bug: Authentication fails on mobile devices",
    "desc": "**Repository:** PlanSync-AI\n\n**Issue Description:**\nUsers are experiencing authentication failures when accessing the application from mobile browsers. The login form submits but returns a 401 error despite correct credentials.\n\n**Steps to Reproduce:**\n1. Open app on mobile browser\n2. Enter valid credentials\n3. Click login button\n\n**Expected Behavior:** Successful authentication\n**Actual Behavior:** 401 Unauthorized error\n\n**Original Issue:** https://github.com/gardo32/PlanSync-AI/issues/123",
    "labels": ["bug", "mobile", "authentication"],
    "urlSource": "https://github.com/gardo32/PlanSync-AI/issues/123"
  }
]
```

Each Trello card includes:
- **Clean, readable title** based on the GitHub issue
- **Enhanced description** with structured formatting
- **Mapped labels** from GitHub to Trello format
- **Direct link** to the original GitHub issue

---

## 🤖 AI Prompt Template

The AI system receives this structured instruction:

> You are an AI agent that processes GitHub issue webhook payloads and converts them into Trello card JSONs.
>
> **Your goals:**
> 1. Analyze the issue JSON data
> 2. Create a concise summary (title and description)
> 3. Generate a valid Trello card JSON containing:
>    - `name`: Clean, readable title
>    - `desc`: Summary including issue body, repo name, and URL
>    - `labels`: Based on GitHub labels (convert to Trello format)
>    - `urlSource`: Link to the original GitHub issue
>
> **Rules:**
> - If the issue body is empty, generate a short placeholder description
> - Always include the GitHub issue URL
> - Ensure the output is strictly valid JSON
> - Enhance clarity while preserving original meaning

---

## ⚙️ Setup Requirements

### GitHub Configuration
1. **Repository Access**: Configure the GitHub Trigger for your repository
2. **Webhook Setup**: n8n automatically creates the webhook endpoint
3. **API Credentials**: Add GitHub API credentials to the workflow

### Trello Configuration
1. **API Access**: Set up Trello API credentials
2. **Board Access**: Ensure access to the target Trello board
3. **List ID**: Find and configure the target list ID in the Variables node

### AI Service
1. **Google Gemini**: Configure API credentials for the AI analysis
2. **Model Selection**: Currently using `gemini-2.5-flash` for fast processing

---

## ✅ Status

* ✅ **Complete** - Fully functional and tested
* Real-time webhook processing working
* AI analysis and enhancement functional
* Trello integration operational
* Error handling and retry logic implemented
* JSON schema validation active
* GitHub repository monitoring configured

---

## 🧭 Next Up

Planned improvements:

* **Bidirectional Sync**: Update GitHub issues when Trello cards change
* **Issue State Mapping**: Handle issue closures, reopening, and state changes
* **Comment Synchronization**: Sync comments between GitHub and Trello
* **Label Management**: Advanced label mapping and creation rules
* **Custom Fields**: Map GitHub metadata to Trello custom fields
* **Bulk Import**: Handle existing issues for new repository setups
* **Notification Channels**: Optional Slack/Teams notifications for new cards

---

## 🔧 Configuration Tips

### Webhook Management
- Verify webhook delivery in GitHub repository settings
- Monitor webhook delivery logs for troubleshooting
- Test with different issue types and content lengths

### AI Optimization
- Adjust AI prompts based on your team's naming conventions
- Fine-tune description formatting for your workflow needs
- Customize label mapping rules for your project categories

### Trello Integration
- Organize lists by priority, status, or project area
- Set up automation rules within Trello for additional processing
- Configure board permissions for team access

### Error Handling
- Monitor n8n execution logs for failed webhook deliveries
- Set up retry mechanisms for API failures
- Configure fallback notifications for critical issues

---

## 🔗 Back to [Main README](../README.md)
