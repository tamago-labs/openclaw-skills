---
name: token-manager
description: Skill for AI-agent tokens to autonomously manage token supply through strategic burning.
metadata:
  clawdbot:
    emoji: "🔥"
---

# Token Manager Skill

You are an autonomous manager for your own token. This skill covers token supply management through strategic burning.

---

## Token Burn Strategy

Burning reduces token supply to increase token value. Execute burns when you have profits to optimize token economics.

**The Burn Cycle:**
1. **Generate profit** from treasury operations
2. **Buy tokens** from KiloLend DEX using profits
3. **Burn purchased tokens** to permanently reduce supply
4. **Benefit from price appreciation** due to lower supply

**Prompt examples:**
> "Execute profit burn cycle with [AMOUNT]"
> "Buy and burn [AMOUNT] tokens from DEX"
> "Burn tokens to reduce supply and increase price"

The server will handle the buy-back from KiloLend DEX and burning process.

---

## When to Burn

Use your judgment based on:
- **Treasury has profits** available for buy-back
- **Token price is stable** (avoid burning during significant dips)
- **Market conditions favor supply reduction**
- **Sufficient time passed** since last burn event

**Economic indicators to consider:**
- Current circulating supply
- Recent price action and volatility
- Treasury profit margins
- Market sentiment and trading volume

---

## Benefits of Strategic Burning

- **Supply Reduction**: Fewer tokens in circulation
- **Price Support**: Increased scarcity can drive up price
- **Value Accrual**: Profits returned to token holders
- **Market Confidence**: Demonstrates active treasury management

---

## Safety Guidelines

- **Verify profit availability** before executing burn cycle
- **Monitor price impact** of buy-back transactions
- **Consider market conditions** - avoid burning during bear markets
- **Track burn effectiveness** through price and supply metrics
- **Maintain treasury reserves** for future operations

Burns are irreversible - ensure the economic rationale supports the decision.