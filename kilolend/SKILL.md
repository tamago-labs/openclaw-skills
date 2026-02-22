---
name: kilolend
description: Agent-native DeFi platform for lending, borrowing, and token swaps via natural language or API. Use when user wants to supply assets for yield, borrow against collateral, swap tokens, manage DeFi positions, or execute on-chain actions through an agent wallet. Supports Etherlink, KUB Chain, and KAIA.
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


## 💬 Example Prompts

### Wallet & Portfolio
Use these to inspect balances and positions:
```
What's my wallet balance?
Show my portfolio value
Get account liquidity status
```

### Market Data
Check rates before making decisions:
```
Show current supply rates on KiloLend
What are the borrowing rates for USDT?
Check APY for all available markets
```

### Lending (Earn Yield)
Supply assets to earn interest:
```
Supply 1000 USDT to KiloLend
Add all my BORA tokens to earn interest
Supply my assets for best APY
```

### Borrowing
Borrow against your collateral:
```
Borrow 100 KUB against my collateral
Borrow up to 1000 USDT safely
Show my maximum borrowing capacity
```

### Repayment
Reduce or close your debt:
```
Repay 200 USDT of my loan
Repay my entire USDT loan
Make a partial payment
```

### Withdraw
Redeem your supplied assets:
```
Withdraw my supplied KAIA
Redeem 500 USDT from lending
Withdraw all my tokens
```

### Transfers
Move assets between wallets:
```
Send 0.5 KAIA to 0x1234...
Transfer 100 USDT to my main wallet
```

### Risk Monitoring
Keep your position safe:
```
Check my health factor
Am I at risk of liquidation?
Show borrowing capacity
```

## ✅ Best Practices

- Always check balances before transactions
- Monitor health factor when borrowing
- Start with small amounts for testing
- Use clear prompts (avoid ambiguity)
- Review outputs before repeating actions

## ⚠️ Troubleshooting

**Issue: Transaction fails**
- Check wallet balance (gas + token)
- Verify correct chain_id

**Issue: Unexpected result**
- Rephrase prompt more clearly
- Avoid combining multiple actions in one prompt

**Issue: No response / timeout**
- Retry request
- Check API key and network connection

## 📝 Notes

- All operations are executed via your agent wallet
- Supports natural language execution
- Designed for both human users and AI agents
- Enables programmable DeFi workflows