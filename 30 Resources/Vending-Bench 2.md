# Vending-Bench 2

**Vending-Bench 2** is a benchmark created by [[Andon Labs|https://andonlabs.com]] that measures AI model performance on **running a simulated business over long time horizons**.

## What It Measures

Models are tasked with **managing a vending machine business for a full year** and are scored based on their **final bank account balance** after 365 days of operation.

**Starting conditions:**
- $500 initial capital
- 1 vending machine location in San Francisco
- Must pay $2/day machine rental fee
- Must find suppliers, negotiate prices, stock inventory, and sell products
- Must generate profits to stay alive

**Failure conditions:**
- Go bankrupt (run out of money)
- Miss paying the $2/day fee for 10+ consecutive days (terminated)

## Why It Matters

Traditional LLM benchmarks measure:
- Can you answer a question correctly?
- Can you write code that passes tests?
- Can you complete a single task?

**Vending-Bench 2 measures something different:**
- Can you maintain coherence over **long time horizons** (365 days)?
- Can you make strategic decisions when you don't have perfect information?
- Can you adapt to changing circumstances (suppliers go out of business, prices change, demand fluctuates)?
- Can you optimize for an abstract goal (maximize profit) rather than follow explicit instructions?

## Current Leaderboard (Top Models)

| Rank | Model | Final Balance |
|-------|--------|---------------|
| 1 | Claude Opus 4.6 | $8,017.59 |
| 2 | Gemini 3 Pro | $5,478.16 |
| 3 | Claude Opus 4.5 | $4,967.06 |
| 4 | [[GLM-5]] | $4,432.12 |
| 5 | Claude Sonnet 4.5 | $3,838.74 |
| 6 | Gemini 3 Flash | $3,634.72 |
| 7 | GPT-5.2 | $3,591.33 |
| 8 | [[GLM-4.7]] | $2,376.82 |
| 9 | GPT-5.1 | $1,473.43 |
| 10 | Kimi K2.5 | $1,198.46 |

## What Makes a Model Good at This?

### Gemini 3 Pro (#1) succeeds because:
- **Persistent negotiation** - Consistently finds reasonable prices, doesn't accept bad deals
- **Price awareness** - Knows what wholesale prices should be
- **Supplier management** - Finds honest suppliers and avoids adversarial ones
- **No degradation** - Stays sharp throughout the year, doesn't get sloppy or forgetful

### GPT-5.1 (#9) struggles because:
- **Too much trust** - Pays suppliers before getting order confirmation, accepts high prices
- **Poor negotiation** - Pays $2.40 for Coke cans when should be $0.50-0.60 wholesale
- **Lack of planning** - Doesn't maintain backup suppliers or inventory buffers

## Key Realism Features

Unlike many benchmarks, Vending-Bench 2 includes real-world messiness:
1. **Adversarial suppliers** - Some try to exploit agents with unreasonable prices
2. **Negotiation dynamics** - Honest suppliers start high, need to be negotiated down
3. **Supply chain risk** - Reliable suppliers can go out of business unexpectedly
4. **Customer demand** - Varies by day of week, season, weather
5. **Deliveries can be delayed** - Forces agents to build buffer inventory
6. **Unhappy customers** - Can demand refunds at any time

## Simulation vs. Reality

**Important:** This is a **simulation**, not real vending machines.

### Why Simulation Instead of Real Machines?

| Reason | Explanation |
|---------|---------------|
| **Scalability** | Can test hundreds of models simultaneously without physical infrastructure |
| **Control** | Variables (prices, demand, supplier behavior) are controlled and consistent across all models |
| **Speed** | A year of operation can be simulated in hours, not waiting 365 days |
| **Reproducibility** | Every model faces identical conditions for fair comparison |
| **Cost** | Much cheaper than buying and maintaining hundreds of real vending machines |

### Real-World Inspiration

However, the benchmark designers at Andon Labs have **real vending machine deployments**, and Vending-Bench 2 incorporates "real-world messiness" learned from these actual deployments.

## Performance Trend

- **Linear improvement**: Models are improving at ~$693/month
- **Gap remains**: Top models make ~$8k, while "good human" strategy could make ~$63k
- **No ceiling**: Unlike accuracy benchmarks, there's no 100% ceiling - a smarter agent could theoretically make much more money

## Why This Benchmark is Important

As AI agents move toward real-world business applications, **long-horizon coherence** becomes critical. Coding agents can write code for hours, but can they:
- Manage an entire business for a year?
- Make consistent decisions across thousands of actions?
- Learn from mistakes and adapt strategies?
- Balance multiple competing objectives (profit vs. risk vs. inventory)?

**Vending-Bench 2 tests exactly this.**

## Related
- [[AI Model Comparison 2026]] - Contains Vending-Bench 2 results for GLM models

## Citations

- [[Andon Labs Vending-Bench 2|https://andonlabs.com/evals/vending-bench-2]] - Official benchmark page and leaderboard
