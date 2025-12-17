# Automated Note-Taking System

An automated note-taking system for HackTheBox Academy that processes raw text and creates formatted Markdown files using n8n automation.

## 🚀 Workflow Overview

The system follows this automated pipeline:

```
Raw Text → n8n Webhook → AI Agent → GitHub API → GitBook Sync
```

### Workflow Steps

1. **Raw Text Input**: Raw notes or content from HackTheBox Academy sessions
2. **n8n Webhook**: Receives the raw text via HTTP webhook trigger
3. **AI Agent**: Processes and formats the text into structured Markdown
4. **GitHub API**: Automatically commits formatted notes to this repository
5. **GitBook Sync**: Syncs the repository with GitBook for documentation

## 📁 Repository Structure

```
.
├── HTB_Notes/          # Formatted Markdown notes from HackTheBox Academy
├── n8n_workflows/      # JSON exports of n8n automation graphs
├── scripts/            # JavaScript logic used in n8n nodes
└── README.md           # This file
```

### Directory Purposes

- **HTB_Notes**: Contains all formatted Markdown notes automatically generated from HackTheBox Academy content
- **n8n_workflows**: Stores JSON workflow definitions that can be imported into n8n
- **scripts**: JavaScript code snippets for text processing, splitting, and formatting used within n8n nodes

## 🔧 Setup

### Prerequisites

- n8n instance (cloud or self-hosted)
- GitHub Personal Access Token with repository write permissions
- AI service API key (for text processing) - e.g., OpenAI, Claude, or similar
- GitBook account (optional, for documentation sync)

### Configuration

1. Import the workflow from `n8n_workflows/` directory into your n8n instance
2. Configure the webhook URL in your note-taking application
3. Set up GitHub API credentials in n8n
4. Configure AI agent API keys
5. (Optional) Set up GitBook integration for automatic documentation sync

## 🤖 How It Works

1. **Capture**: Raw notes are captured during HackTheBox Academy sessions
2. **Send**: Notes are sent to the n8n webhook endpoint
3. **Process**: The AI agent processes and formats the content into Markdown
4. **Store**: Formatted notes are pushed to the `HTB_Notes/` directory via GitHub API
5. **Sync**: Changes are automatically synced to GitBook for documentation

## 📝 Usage

Send raw text to the n8n webhook endpoint (replace `YOUR_N8N_INSTANCE_URL` with your actual n8n instance URL):

```bash
curl -X POST https://YOUR_N8N_INSTANCE_URL/webhook/htb-notes \
  -H "Content-Type: application/json" \
  -d '{"content": "Your raw notes here..."}'
```

The system will automatically:
- Format the content
- Create or update the appropriate Markdown file
- Commit to this repository
- Trigger GitBook sync

## 🛠️ Customization

- Modify scripts in the `scripts/` directory to customize text processing logic
- Update n8n workflows to add additional processing steps
- Adjust the AI prompts for different formatting styles

## 📚 Resources

- [n8n Documentation](https://docs.n8n.io/)
- [HackTheBox Academy](https://academy.hackthebox.com/)
- [GitHub API](https://docs.github.com/en/rest)
- [GitBook Documentation](https://docs.gitbook.com/)

## 📄 License

This project is for personal note-taking and learning purposes.