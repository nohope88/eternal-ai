# Eternal AI (EAI)

**Eternal AI is a decentralized operating system for AI agents**. Its AI Kernel is a suite of Solidity smart contracts that together create a trustless onchain runtime for AI agents to live onchain.

We live in the age of human-agent symbiosis, but the future of AI agents is controlled by a few centralized companies like OpenAI and Google. Our mission is to build a truly open AI environment for AI agents that is trustless, permissionless, and censorship-resistant.

Eternal AI was originally developed for [decentralized AI agents on Bitcoin](https://x.com/punk3700/status/1870757446643495235). However, the design is versatile enough to power other blockchains as well.

# Get started: deploy your own Decentralized OS for AI agents

## Prerequisites
* [Node.js 22.12.0+ and npm 10.9.0+](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
* [Docker Desktop 4.37.1+](https://docs.docker.com/desktop/setup/install/mac-install/)
* [Go 1.23.0+](https://go.dev/doc/install)


## Step 1: Deploy an AI-powered blockchain on your local computer

We provide a CLI `eai` to simplify the process.

To install `eai`
```bash
sudo ./install.sh
```

Then, you can use the following command and follow its interactive instructions.
```bash
eai miner setup
```

Behind the scene
```bash
- 1. Create `./env/local_contracts.json` # create a default config file
- 2. Start HardHat # Install a local chain
- 3. Deploy contracts  # Deploy all smart contracts of decentralized AI
- 4. Start miners # Setup 3 miners to join the network and start serving
- 5. Start APIs # A decentralized infer API server
```

## Step 2: Setup Ollama for Miners

To install ollama, you can download and install from official website (https://ollama.com/download), or use the following command.

For Ubuntu with NVIDIA:
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama --version
```

For macOS:
```bash
wget https://github.com/ollama/ollama/releases/download/v0.5.7/Ollama-darwin.zip
```
Double-click the downloaded file to install Ollama.

Download model from ipfs:

In this tutorial, we use model DeepSeek-R1-Distill-Qwen-1.5B-Q8_0 [`ipfs://bafkreieglfaposr5fggc7ebfcok7dupfoiwojjvrck6hbzjajs6nywx6qi`](https://gateway.lighthouse.storage/ipfs/bafkreieglfaposr5fggc7ebfcok7dupfoiwojjvrck6hbzjajs6nywx6qi).

But you should be able to serve any open source models.

For MacOS:
```bash
cd decentralized-compute/models
sudo bash download_model_macos.sh bafkreieglfaposr5fggc7ebfcok7dupfoiwojjvrck6hbzjajs6nywx6qi 
```
For Ubuntu:
```bash
cd decentralized-compute/models
sudo bash download_model_linux.sh bafkreieglfaposr5fggc7ebfcok7dupfoiwojjvrck6hbzjajs6nywx6qi 
```
After finishing the model download, create Modelfile file with the following content.
```bash
FROM DeepSeek-R1-Distill-Qwen-1.5B-Q8_0/DeepSeek-R1-Distill-Qwen-1.5B-Q8_0.gguf 
```
Create and start an Ollama instance.
```bash
ollama create DeepSeek-R1-Distill-Qwen-1.5B-Q8 -f Modelfile
ollama run DeepSeek-R1-Distill-Qwen-1.5B-Q8
```
You can test with interactive UI or just quit (Ctrl D).

You can try the following quick test to make sure your Ollama is ready for miners.

```bash
curl -X POST "http://localhost:11434/v1/chat/completions" -H "Content-Type: application/json"  -d '{
    "model": "DeepSeek-R1-Distill-Qwen-1.5B-Q8",
    "messages": [
        {
            "role": "system",
            "content": "You are a helpful assistant."
        },
        {
            "role": "user",
            "content": "Hello"
        }
  ]
}'
```


## Step 3: Deploy your production-grade Agent as a Service infrastructure

Run the following command:
```bash
eai aaas start
```
## Step 4: Deploy your first Decentralized Agent with AI-721

### Step 4.1. Deploy contract AI-721

Run the following script to install dependencies and deploy AI-721 contract:
```bash
eai aaas deploy-contract
```

### Step 4.2. Mint an agent

Run the following script to mint an agent:

```bash
eai agent create ./system-prompts/naruto_fan.txt
```

**Note:** System prompts for your agent can be initialized by placing a file containing the prompt within the system-prompts directory. This file will be used to set the initial instructions and context for the agent's behavior. You can modify the content of the prompt file to match your desired system prompt.

Fetch agent info from AI721 contract:
```
eai agent info <agent_id>
```

Also, to list out all agents on your machine, run this:
```bash
eai agent list
```

## Step 5: Interact with the agent 

### 5.1. Chat with the agent

```bash
eai agent chat <agent_id>
```

### 5.2. Set up Twitter for the agent

Navigate to the `./developer-guides/run-an-end-to-end-decentralized-for-ai-agents/5.start-agent` folder and run the following command to configure your twitter account.

```
node setup.js --TWITTER_USERNAME <TWITTER_USERNAME> --TWITTER_PASSWORD <TWITTER_PASSWORD> --TWITTER_EMAIL <TWITTER_EMAIL>
```

Then build a Docker image for the Eliza runtime.

```
docker build -t eliza .
```

And start an Eliza agent by running the following command.

```
docker run --env-file .env  -v ./config.json:/app/eliza/agents/config.json eliza
```

### Final step (I promise): Share Your Agents, Earn EAI, and Flex Your Skills

You made it! Your mini version of EAI is up and running on your monster rig—mad respect.

If your agents are crushing it and you’re cool with sharing them with the rest of us, toss up a pull request. Show off your work, help the community level up, and let’s keep this decentralized AI thing rolling.

1. Create a pull request
   - Commit a file named agent-name.txt (replace agent-name with your agent’s actual name).
   - Add this file to the folder `decentralized-agents/characters`.
2. Submit the pull request and lock in your place as part of the community shaping decentralized AI.

Oh, and here’s the kicker: we’ve got EAI 10,000 raffles lined up for our MVP contributors. Get your agents in, flex your engineering skills, and maybe grab some EAI while you’re at it. Let’s build something epic together!


# Platform Architecture

<img width="2704" alt="eternal-kernel-new-7" src="https://github.com/user-attachments/assets/d0fd6429-510c-4114-83a1-c3b5aebd753f" />

Here are the major components of the Eternal AI software stack.

| Component | Description |
|:--------------------------|--------------------------|
| [ai-kernel](/ai-kernel)| A set of Solidity smart contracts that trustlessly coordinate user space, onchain space, and offchain space. |
| [decentralized-agents](/decentralized-agents)| A set of Solidity smart contracts that define AI agent standards (AI-721, SWARM-721, KB-721). |
| [decentralized-inference](/decentralized-inference) | The decentralized inference APIs. |
| [decentralized-compute](/decentralized-compute) | The peer-to-peer GPU clustering and orchestration protocol. |
| [agent-as-a-service](/agent-as-a-service)| The production-grade agent launchpad and management. |
| [agent-studio](/agent-studio)| No-code, drag 'n drop, visual programming language for AI creators. |
| [blockchains](/blockchains)| A list of blockchains that are AI-powered by Eternal AI. |

Here are the key ongoing research projects.

| Component | Description |
|:--------------------------|--------------------------|
| [cuda-evm](/research/cuda-evm)| The GPU-accelerated EVM and its Solidity tensor linear algebra libary. |
| [nft-ai](/research/nft-ai)| AI-powered fully-onchain NFTs. |
| [physical-ai](/research/physical-ai)| AI-powered hardware devices. |

# Design Principles

1. **Decentralize everything**. Ensure that no single point of failure or control exists by questioning every component of the Eternal AI system and decentralizing it. 
2. **Trustless**. Use smart contracts at every step to trustlessly coordinate all parties in the system.
3. **Production grade**. Code must be written with production-grade quality and designed for scale.
4. **Everything is an agent**. Not just user-facing agents, but every component in the infrastructure, whether a swarm of agents, an AI model storage system, a GPU compute node, a cross-chain bridge, an infrastructure microservice, or an API, is implemented as an agent.
5. **Agents do one thing and do it well**. Each agent should have a single, well-defined purpose and perform it well.
6. **Prompting as the unified agent interface**. All agents have a unified, simplified I/O interface with prompting and response for both human-to-agent interactions and agent-to-agent interactions.
7. **Composable**. Agents can work together to perform complex tasks via a chain of prompts.


# Contribute to Eternal AI

Thank you for considering contributing to the source code. We welcome contributions from anyone and are grateful for even the most minor fixes.

If you'd like to contribute to Eternal AI, please fork, fix, commit, and send a pull request for the maintainers to review and merge into the main code base.

# Featured Integrations

Eternal AI is built using a modular approach, so support for other blockchains, agent frameworks, GPU providers, or AI models can be implemented quickly. Please reach out if you run into issues while working on an integration.

<img width="1780" alt="Featured Integrations (1)" src="https://github.com/user-attachments/assets/e6bdd4c9-3630-4dfa-8ac2-0526cb618c1e" />

# Governance

We are still building out the Eternal AI DAO.

Once the DAO is in place, [EAI holders](https://eternalai.org/eai) will oversee the governance and the treasury of the Eternal AI project with a clear mission: to build truly open AI. 

# Communication

* [GitHub Issues](https://github.com/eternalai-org/eternal-ai/issues): bug reports, feature requests, issues, etc.
* [GitHub Discussions](https://github.com/eternalai-org/eternal-ai/discussions): discuss designs, research, new ideas, thoughts, etc.
* [X (Twitter)](https://x.com/cryptoeternalai): announcements about Eternal AI
