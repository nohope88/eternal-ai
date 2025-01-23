# Eternal AI (EAI)

We live in the age of human-agent symbiosis, but the future of AI agents is controlled by a few centralized companies. What is needed is a decentralized environment for AI agents that is trustless, censorship-resistant, and permissionlessly accessible to anyone.

## The Decentralized Operating System for AI Agents

Eternal AI, also known as EAI, is an open source decentralized operating system for AI agents. Its AI Kernel is a suite of smart contracts that together create a trustless onchain runtime for AI agents to live onchain.

Eternal AI was originally developed in Jan 2023 by AI researchers at Eternal AI and protocol engineers at Bitcoin Virtual Machine to build [fully onchain AI on Bitcoin](https://x.com/punk3700/status/1870757446643495235). However, the design is versatile enough to power other blockchains as well.

Use the open source Eternal AI decentralized operating system to power your blockchain. Eternal AI has been battle-tested on the largest blockchains, including Bitcoin, Ethereum, Solana, Base, Arbitrum, ZK, BNB Chain, ApeChain, Avalanche, Tron, Polygon, Abstract, and Bittensor.

<img width="2704" alt="eternal-kernel-new-7" src="https://github.com/user-attachments/assets/d0fd6429-510c-4114-83a1-c3b5aebd753f" />

## Design Principles

1. **Decentralize everything**. Ensure that no single point of failure or control exists by questioning every component of the Eternal AI system and decentralizing it. 
2. **Trustless**. Use smart contracts at every step to trustlessly coordinate all parties in the system.
3. **Production grade**. Code must be written with production-grade quality and designed for scale.
4. **Everything is an agent**. Not just user-facing agents, but every component in the infrastructure, whether a swarm of agents, an AI model storage system, a GPU compute node, a cross-chain bridge, an infrastructure microservice, or an API, is implemented as an agent.
5. **Agents do one thing and do it well**. Each agent should have a single, well-defined purpose and perform it well.
6. **Prompting as the unified agent interface**. All agents have a unified, simplified I/O interface with prompting and response for both human-to-agent interactions and agent-to-agent interactions.
7. **Composable**. Agents can work together to perform complex tasks via a chain of prompts.

## Navigate the Source Code

Here are the major components of the Eternal AI software stack.

| Component | Description |
|:--------------------------|--------------------------|
| [decentralized-agents](/decentralized-agents)| A set of smart contract standards for decentralized AI agents (AI721s). |
| [ai-kernel](/ai-kernel)| A set of smart contracts that trustlessly coordinate the infrastructure operations. |
| [decentralized-inference](/decentralized-inference) | A set of smart contracts that together perform onchain-verifiable inference. |
| [decentralized-compute](/decentralized-compute) | A set of smart contracts that orchestrate GPU resources. |
| [agent-as-a-service](/agent-as-a-service)| The production-grade agent launchpad and management. |
| [blockchains](/blockchains)| A list of blockchains that are AI-powered by Eternal AI |
| [creator-tools](/creator-tools)| No-code tools for AI creators to create and manage their agents. |

Here are the key ongoing research projects.

| Component | Description |
|:--------------------------|--------------------------|
| [cuda-evm](/research/cuda-evm)| GPU-accelerated EVM for AI |
| [nft-ai](/research/nft-ai)| AI-powered fully-onchain NFTs |
| [physical-ai](/research/physical-ai)| AI-powered hardware devices |

## Getting Started

Let's deploy your own decentralized operating system for AI agents.

**Step 1: Deploy a local blockchain for development**

TODO: Write

**Step 2: Deploy your first Decentralized Compute cluster**

TODO: Write

**Step 3: Deploy your production-grade Agent as a Service infrastructure**

Open a new terminal and navigate to the `./agent-as-a-service/agent-orchestration/backend` folder.

Run the following command to build a docker image for the service:
```bash
docker-compose build
```
Run the following command to run the service:
```bash
docker-compose up
```

**Step 4: Deploy your first Decentralized Agent with AI-721**

***Step 4.1 Deploy contract AI-721***

Open a new terminal and navigate to the `./developer-guides/run-an-end-to-end-decentralized-for-ai-agents/4.how-to-deploy-and-mint-agent` folder.

Run the following script to install dependencies and deploy AI-721 contract:
```bash
./deploy-ai721.sh
```

***Step 4.2 Mint an agent***

Run the following script to mint an agent:

```bash
./mint-agent.sh ./prompt.txt  
```

**Note:** You can modify the content of the `prompt.txt` file to match your desired system prompt.

Also, to list out all agents on your machine, run this:
```bash
./ls-agents.sh
```

**Step 5.1: Start an EternalAI Agent**

**Step 5.2: Start an Eliza Agent**

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


## Contribute to Eternal AI

Thank you for considering contributing to the source code. We welcome contributions from anyone and are grateful for even the most minor fixes.

If you'd like to contribute to Eternal AI, please fork, fix, commit, and send a pull request for the maintainers to review and merge into the main code base.

If you wish to submit more complex changes, please first check with the core developers to ensure they align with the project's general philosophy and get some early feedback. This can make your efforts and our review and merge procedures quick and simple.

## Communication

* [GitHub Issues](https://github.com/eternalai-org/truly-open-ai/issues): bug reports, feature requests, issues, etc.
* [GitHub Discussions](https://github.com/eternalai-org/truly-open-ai/discussions): discuss designs, research, new ideas, thoughts, etc.
* [X (Twitter)](https://x.com/cryptoeternalai): announcements about Eternal AI
