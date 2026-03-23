# 🚀 PyRun: AWS & GitHub Copilot Integration

PyRun bridges the gap between your cloud infrastructure and your terminal using the power of AI. By integrating GitHub Copilot CLI with a pre-configured MCP (Model Context Protocol) server, PyRun allows you to manage your entire AWS ecosystem through simple, natural language conversations.

## ✨ The Philosophy of Simplicity

At PyRun, we believe that cloud management shouldn't be a hurdle. Simplicity is our core identity. 

We have engineered an AI-guided process that eliminates the complexity of traditional setups. There are no configuration files to edit, no manual environment variables to map, and no complex installation steps. PyRun handles the heavy lifting behind the scenes so you can focus on building, not configuring.

## 🚀 Getting Started

To launch the integrated system, simply open your terminal and type:

```bash
copilot
```

This command initializes the GitHub Copilot CLI with full awareness of your AWS account. From this single interface, you can immediately start interacting with your cloud resources (Lambda, EC2, S3, ...).

## 💻 VSCode Integration

If you prefer working directly in your editor, you can use Copilot through our pre-installed VSCode extension. Simply sign in to your GitHub account and it will start working instantly.

**⚠️ Important Note:** When signing in, you might encounter the following error pop-up:

> *An error occurred while setting up chat. Would you like to try again?*
> *The extension 'GitHub.copilot-chat' cannot be installed because it was not found.*

**This is completely normal.** Please ignore this message and click **Cancel**. The extension is already successfully installed in the background and will work perfectly with our MCP server without any further action.

## 🤖 OpenCode Agent

Additionally, PyRun includes another powerful AI agent called **[OpenCode](https://opencode.ai/)**. It is also fully installed and ready to use right out of the box. 

To start interacting with it, simply run:

```bash
opencode
```

## 🧰 SKILLS.sh Integration
PyRun now includes out-of-the-box support for **[SKILLS.sh](https://skills.sh/)** (powered by Vercel Agent Skills). This integration expands your AI agents' capabilities, allowing them to interact with an even wider array of tools and perform complex tasks directly from your environment.

The skills ecosystem is pre-configured, meaning your agents can start utilizing these extended functionalities immediately to streamline your workflow without any manual setup.

## 🛠️ Capabilities

Since PyRun comes with a built-in MCP server already connected to your AWS environment, you can use natural language to:

*   **Create & Deploy:** Provision new resources (S3 buckets, EC2 instances, Lambda functions) instantly.
*   **Read & Query:** Ask questions about your architecture and get real-time data.
*   **Monitor:** Track system health and view logs without leaving the terminal.
*   **Manage:** Update or delete existing infrastructure with simple verbal instructions.

*PyRun: Cloud management, simplified by AI.*