# Production AI Agents on Azure with Microsoft Foundry

A hands-on notebook series for building, deploying, and managing production-grade AI agents using **Microsoft Foundry** (formerly Azure AI Foundry) and **Azure App Service**.

## What You'll Learn

Build an end-to-end AI agent application — from provisioning Azure resources to deploying a Chainlit-powered conversational app with GPT-4o, complete with managed identity, tools, and enterprise patterns.

## Notebooks

| # | Notebook | Topics |
|---|----------|--------|
| 01 | [Prerequisites & Setup](01_prerequisites_and_setup.ipynb) | Azure AI Hub/Project creation, GPT-4o deployment, environment setup, Chainlit app configuration |
| 02 | [What is Microsoft Foundry?](02_what_is_microsoft_foundry.ipynb) | Platform overview, resource model, 1,900+ models, Responses API, SDKs, first API call |
| 03 | [Create Resources & First Agent](03_create_resources_and_first_agent.ipynb) | Foundry resources via Azure CLI, model deployment, RBAC, agent creation, multi-turn conversations, enterprise patterns (SharePoint + MCP + Evaluation) |
| 04 | [Agent Lifecycle, Tools & Identity](04_agent_lifecycle_tools_and_identity.ipynb) | 8-step lifecycle, agent types (Prompt/Workflow/Hosted), identity & OAuth, RAG & vector stores, tool catalog, Azure AI Search, Code Interpreter, function calling |
| 05 | [Advanced Tools & Integrations](05_advanced_tools_and_integrations.ipynb) | Advanced tooling, MCP servers, OpenAPI integration, multi-agent orchestration, production monitoring |

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Azure Cloud                          │
│                                                         │
│  ┌──────────────────┐     ┌──────────────────────────┐  │
│  │  Azure App        │     │  Azure AI Foundry Hub     │  │
│  │  Service          │────>│                          │  │
│  │  (Chainlit App)   │     │  ┌────────────────────┐  │  │
│  │                   │     │  │  AI Foundry Project │  │  │
│  └──────────────────┘     │  │                    │  │  │
│         │                  │  │  ┌──────────────┐ │  │  │
│         │ Managed          │  │  │  Agent        │ │  │  │
│         │ Identity         │  │  │  (GPT-4o)    │ │  │  │
│         │                  │  │  └──────────────┘ │  │  │
│         v                  │  └────────────────────┘  │  │
│  ┌──────────────────┐     │                          │  │
│  │  Azure OpenAI     │<────│  Models + Endpoints      │  │
│  │  (gpt-4o model)  │     └──────────────────────────┘  │
│  └──────────────────┘                                   │
└─────────────────────────────────────────────────────────┘
```

## Prerequisites

- **Azure Subscription** ([Create free account](https://azure.microsoft.com/free/))
- **Python 3.12+**
- **Azure CLI** ([Install](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli))
- **Git**

## Quick Start

1. Clone this repository:
   ```bash
   git clone <repo-url>
   cd agent-production-azure
   ```

2. Install dependencies:
   ```bash
   pip install azure-ai-projects azure-identity openai chainlit python-dotenv
   ```

3. Log in to Azure:
   ```bash
   az login
   ```

4. Create a `.env` file with your credentials:
   ```env
   AIPROJECT_CONNECTION_STRING=your_connection_string_here
   AGENT_ID=your_agent_id_here
   PROJECT_ENDPOINT=https://<resource_name>.ai.azure.com/api/projects/<project_name>
   ```

5. Open the notebooks in order, starting with `01_prerequisites_and_setup.ipynb`.

## Key Technologies

- **Microsoft Foundry** -- Unified Azure PaaS for agents, models, and tools
- **Azure AI Projects SDK** (`azure-ai-projects` 2.x) -- Unified SDK for Foundry APIs
- **Responses API** -- Agent-native API replacing Chat Completions
- **Chainlit** -- Python-based conversational UI
- **Azure App Service** -- Hosting with managed identity and auto-scaling

## Resources

- [Microsoft Foundry Portal](https://ai.azure.com)
- [Azure AI Agent Service Documentation](https://learn.microsoft.com/en-us/azure/ai-services/agents/overview)
- [Azure AI Projects SDK (PyPI)](https://pypi.org/project/azure-ai-projects/)
- [Chainlit Documentation](https://docs.chainlit.io/)
- [Foundry Samples Repository](https://github.com/microsoft-foundry/foundry-samples)
