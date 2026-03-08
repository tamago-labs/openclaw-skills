# OpenClaw Skills

Pre-built capabilities for AI agents to interact with real-world systems through natural language.

This repository provides structured **skills** that agents can read, understand, and execute — powered by KiloLend and the OpenClaw ecosystem.

---

## 🚀 Quick Start

Add this repository to your agent runtime:

```bash
https://github.com/tamago-labs/openclaw-skills
```

Agents will automatically discover and use available skills via SKILL.md.

## 🧠 What is KiloLend?

KiloLend is an agent-native DeFi platform that enables lending, borrowing, and token swaps through natural language.

It provides:
- Agent wallets for execution
- API-based access to on-chain actions
- Natural language interface for DeFi operations

## 📦 Available Skills

| Skill | Description |
| ----- | ----------- |
| [kilolend](kilolend/) | Execute DeFi actions (lend, borrow, swap, manage portfolio) using natural language on Etherlink, KUB Chain, and KAIA |
| [token-manager](token-manager/) | Autonomously manage token supply through strategic burning using profits to reduce supply and increase token price |

## ⚙️ How It Works

1. **Agents read SKILL.md** to understand capabilities
2. **Agents configure required authentication** (e.g. API keys)
3. **Agents execute actions** using natural language prompts
4. **Transactions are performed** via agent wallets on-chain

## 🏗 Structure

```
openclaw-skills/
├── kilolend/
│   └── SKILL.md
├── token-manager/
│   └── SKILL.md
└── README.md
```

Each skill includes:
- **SKILL.md** — instructions, API usage, and prompt examples

## ➕ Adding a New Skill

1. **Create a new directory:**
   ```bash
   your-skill/
   ```

2. **Add SKILL.md:**
   ```yaml
   ---
   name: your-skill
   description: What it does
   metadata:
     clawdbot:
       emoji: "🔧"
   ---
   ```

3. **Include:**
   - Setup instructions
   - API usage (if applicable)
   - Example prompts
   - Best practices

4. **Submit a pull request**

## 📌 Guidelines

- Keep instructions clear and concise
- Design for natural language execution
- Include real, working examples
- Ensure secure handling of keys and transactions
- Optimize for both AI agents and developers

## 🌐 Vision

OpenClaw Skills + KiloLend enable a new paradigm:

AI agents that can understand, decide, and act on-chain using natural language.