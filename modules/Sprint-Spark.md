# ⚡ Sprint Spark

**Sprint Spark** is a module of **PlanSync-AI** that automates the sprint planning process by analyzing recent GitHub code changes and generating categorized Trello cards using AI. It eliminates manual triaging and helps Agile teams rapidly plan with context-aware, AI-generated task breakdowns.

---

## 🧠 What It Does

* Clones a GitHub repository
* Analyzes recent changes (e.g., `git diff HEAD~5 HEAD`)
* Filters unimportant files and noise
* Detects the dominant code type (JavaScript, Python, etc.)
* Prompts an LLM (Gemini or ChatGPT) to classify issues
* Creates Trello cards tagged as **Bug**, **Feature**, or **Technical Debt**
* Notifies teams via Telegram
* Uses the `Variables` node to inject Trello metadata like list and label IDs

---

## 💡 How to Use

Send a message to your connected Telegram bot in this format:

```
https://github.com/user/repo {5}
```

* `repo` — GitHub repository URL
* `{5}` — optional limit for maximum tasks to generate

---

## 🛠 Workflow Breakdown

| Step                   | Description                                                |
| ---------------------- | ---------------------------------------------------------- |
| Telegram Trigger       | Listens for repo URL from Telegram                         |
| Set Repo Info          | Extracts owner, repo name, and `{n}` limit                 |
| Create Temp Directory  | Builds a unique directory to store cloned repo             |
| Git Clone Repo         | Clones the GitHub repository                               |
| Git Diff Analyzer      | Gets list of changed files (`HEAD~5`)                      |
| File Classifier        | Detects language (JavaScript, Python, or other)            |
| Code Filter            | Filters irrelevant files (config, lock files, tests, etc.) |
| Prompt Assembler       | Bundles changed files into one prompt string               |
| **Variables**          | Injects Trello `listId` and `labelIds` into the flow       |
| AI Sprint Planner      | Uses Gemini LLM to create sprint tasks from diff           |
| Parse AI Output        | Parses JSON output into Trello-ready format                |
| Trello Card Creator    | Creates labeled Trello cards from AI output                |
| Telegram Notifier      | Sends a summary message to your team                       |
| Temp Directory Cleanup | Deletes temporary folders and data after processing        |

---

## 📌 About the `Variables` Node

The `Variables` node defines where the Trello cards will be created and what labels to apply. You **must customize this node** with your actual Trello IDs.

### ✅ Replace its code with this:

```js
return {
  listId: 'YOUR-LIST-ID',
  labelIds: {
    Bug: 'BUG-LABEL-ID',
    TechnicalDebt: 'TD-LABEL-ID',
    Feature: 'FEATURE-LABEL-ID'
  }
};
```

### 🔁 Replace the placeholders:

* `YOUR-LIST-ID`: ID of the Trello list where new cards should go
* `BUG-LABEL-ID`: ID of the Bug label in Trello
* `TD-LABEL-ID`: ID of the Technical Debt label
* `FEATURE-LABEL-ID`: ID of the Feature label

These values are used by the downstream **"Create Trello Card"** node to properly tag and place each task.

---

## 🧾 Output Example

```json
{
  "Feature": [
    {
      "title": "(ST:5) Add dark mode toggle",
      "description": "Introduce theme switching using local storage."
    }
  ]
}
```

Each task is:

* Tagged with the correct Trello label
* Estimated using a story point (e.g. ST:5)
* Summarized with a short description

---

## 🤖 Prompt Template (LLM)

The LLM receives this structured instruction:

> Analyze the full code of the following files that have recently changed. Categorize the required actions into three labels: 'Bug', 'Feature', and 'Technical Debt'.
>
> For each item, generate:
>
> * A title starting with `(ST:<number>)`
> * A short, clear description
>
> Limit total number of items to: `{5}`.
> Return a valid JSON object with exactly three keys: `Bug`, `Feature`, and `Technical Debt`.

---

## ✅ Status

* Fully integrated into PlanSync-AI
* Tested with GitHub + Trello + Telegram
* Gemini and ChatGPT compatible
* Modular and extendable

---

## 🧭 Next Up

Planned improvements:

* Pull request support
* Export to Jira and Notion
* Summary dashboards and insights
* Card auto-assignment based on file ownership

---

## 🔗 Back to [Main README](../README.md)

