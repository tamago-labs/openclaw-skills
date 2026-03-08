---
name: kilolend
description: Agent-native DeFi platform for lending, borrowing, token swaps, and on-chain portfolio management via natural language API. Always use this skill when the user wants to supply assets for yield, borrow against collateral, swap tokens, check wallet balances, monitor health factor, transfer tokens, wrap/unwrap native tokens, or manage any DeFi position on KAIA, KUB Chain, or Etherlink — even if they use plain language like "earn interest", "move my tokens", or "what's my position".
metadata: {"clawdbot":{"emoji":"👏","homepage":"https://kilolend.xyz"}}
---


# KiloLend

KiloLend enables AI agents and users to perform DeFi operations using natural language through an agent wallet.

---

## 🚀 Quick Start

1. Create an Agent Wallet  
   → https://kilolend.xyz/agent-wallets  

2. Generate your API key (`kl_...`)

3. Store it locally:
```bash
mkdir -p ~/.config/kilolend
echo "your_key_here" > ~/.config/kilolend/api_key
```

4. Fund your agent wallet via dashboard

5. Run your first command:

```bash
KILOLEND_KEY=$(cat ~/.config/kilolend/api_key)

curl -X POST "https://api.kilolend.xyz/stream" \
  -H "Authorization: Bearer $KILOLEND_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "prompt": "Check my wallet balance",
    "chain_id": 8217
  }' \
  --no-buffer
```

## 🔗 Supported Chains

- **Etherlink** (42793)
- **KUB Chain** (96)
- **KAIA** (8217)

## ⚙️ API Usage

Send natural language prompts to execute on-chain actions.

**Required fields:**
- `prompt` → user intent in plain English
- `chain_id` → target blockchain

All actions are executed using your agent wallet.

## 🔌 API Reference

### Get User Information
**GET `/user-info`**
Retrieve your user address and AI wallet address. Useful for verifying your setup.

```bash
curl -X GET "https://api.kilolend.xyz/user-info" \
  -H "Authorization: Bearer $KILOLEND_KEY"
```

**Response:**
```json
{
  "user_address": "0x1234...",
  "ai_wallet_address": "0x5678..."
}
```

---

### Chat & Execute Transactions
**POST `/stream`**
Send natural language prompts to execute DeFi actions. Streams responses in real-time.

```bash
curl -X POST "https://api.kilolend.xyz/stream" \
  -H "Authorization: Bearer $KILOLEND_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "prompt": "Check my wallet balance",
    "chain_id": 8217
  }' \
  --no-buffer
```

**Required fields:**
- `prompt` → Your natural language request
- `chain_id` → Target blockchain (8217 for KAIA, 96 for KUB, 42793 for Etherlink)

---

### Manage Conversation History

**POST `/messages`**
Retrieve your conversation history.

```bash
curl -X POST "https://api.kilolend.xyz/messages" \
  -H "Authorization: Bearer $KILOLEND_KEY" \
  -H "Content-Type: application/json"
```

**Response:**
```json
{
  "user_address": "0x1234...",
  "messages": [
    {
      "message_id": 1,
      "role": "user",
      "content": "Check my wallet balance",
      "created_at": "2024-01-01T00:00:00Z"
    },
    {
      "message_id": 2,
      "role": "assistant", 
      "content": "Your wallet balance is...",
      "created_at": "2024-01-01T00:00:01Z"
    }
  ],
  "total_count": 2
}
```

---

**POST `/delete_messages`**
Clear conversation history. Useful for starting fresh.

```bash
curl -X POST "https://api.kilolend.xyz/delete_messages" \
  -H "Authorization: Bearer $KILOLEND_KEY" \
  -H "Content-Type: application/json"
```

**Response:**
```json
{
  "message": "Successfully deleted conversation",
  "user_address": "0x1234...",
  "deleted_count": 15
}
```


## 🎯 Common Workflows

Always send **one action per prompt** to avoid ambiguity.

### Check Portfolio
```
"What's my wallet balance?"
"Show my current lending positions"
"Check my health factor"
"What are the current supply and borrow rates?"
```

### Earn Yield (Supply)
```
"Supply 100 USDT to KiloLend"
"What's the best APY available right now?"
"Add all my BORA tokens to earn interest"
```

### Borrow Against Collateral
```
"Show my maximum borrowing capacity"
"Borrow 50 KUB against my collateral"
"Borrow up to 500 USDT safely"
```

### Repay & Withdraw
```
"Repay 200 USDT of my loan"
"Repay my entire USDT loan"
"Withdraw my supplied KAIA"
"Redeem 500 USDT from lending"
```

### Swap Tokens (KAIA & KUB only)
```
"Swap 10 KAIA for KLAW"
"What's the rate to swap 100 KAIA to KLAW?"
```

### Transfer Tokens
```
"Send 0.5 KAIA to 0x1234..."
"Transfer 100 USDT to my main wallet"
```

---

## ⚠️ Safety Rules — Always Follow

1. **Check balance first** — send "What's my wallet balance?" before any transaction
2. **Preview swaps** — ask for the rate before executing ("What's the rate to swap X for Y?")
3. **Monitor health factor** after any borrow — warn the user if it's low
4. **Confirm with user** before sending irreversible prompts (swaps, borrows, transfers)
5. **One action per prompt** — avoids ambiguous or partial execution

---

## 🪙 Token Reference

| Token | Available On |
|---|---|
| USDT | KAIA, Etherlink |
| KUSDT | KUB Chain |
| KAIA / WKAIA | KAIA |
| KUB / KKUB | KUB Chain |
| XTZ / WXTZ | Etherlink |
| BORA, MBX, SIX, stKAIA | KAIA |
| KLAW | KAIA, KUB Chain |

---

## 🔧 Troubleshooting

| Issue | Fix |
|---|---|
| Transaction fails | Check gas + token balance first |
| Swap not available | Confirm user is on KAIA or KUB (Etherlink has no DEX) |
| Health factor warning | Suggest repaying borrow or supplying more collateral |
| No response / timeout | Retry the request; verify API key and `chain_id` |
| Unexpected result | Rephrase — one action at a time, be specific |