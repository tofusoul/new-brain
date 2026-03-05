# AI Model Comparison 2026: GLM, Claude, Gemini, Kimi, GPT, MiniMax

## GLM 4.7 vs GLM 5 - Key Differences

### Architecture
| Aspect | GLM 4.7 | GLM 5 |
|--------|----------|--------|
| Parameters | Not fully disclosed | 744B total / 40B active (MoE) |
| Training Data | 23T tokens | 28.5T tokens |
| Architecture | GLM with Interleaved Thinking | Enhanced MoE with DeepSeek Sparse Attention (DSA) |
| Context Window | 200K tokens | 200K+ with DSA optimization |

### Benchmark Comparison (Hugging Face Data)
| Benchmark              | GLM 4.7   | GLM 5     | Winner |
| ---------------------- | --------- | --------- | ------ |
| HLE                    | 24.8      | 30.5      | GLM 5  |
| HLE (w/ Tools)         | 42.8      | 50.4      | GLM 5  |
| SWE-bench Verified     | 73.8      | 77.8      | GLM 5  |
| SWE-bench Multilingual | 66.7      | 73.3      | GLM 5  |
| Terminal-Bench 2.0     | 41.0      | 56.2      | GLM 5  |
| BrowseComp             | 52.0      | 62.0      | GLM 5  |
| CyberGym               | 23.5      | 43.2      | GLM 5  |
| Vending Bench 2        | $2,376.82 | $4,432.12 | GLM 5  |

### Latency & Performance (WaveSpeedAI)
| Metric | GLM 4.7 | GLM 5 |
|--------|----------|--------|
| 50 tokens | ~120ms | ~150ms |
| 300 tokens | ~420ms | ~450ms |
| 1,200 tokens | ~1,800ms | ~1,650ms |

**Key Insight**: GLM-5 adds overhead for short queries but outperforms on longer outputs due to MoE efficiency.

## GLM 5 vs Other Leading Models

### Benchmark Rankings (Best to Worst)

#### Reasoning (HLE)
1. Gemini 3 Pro: 37.2
2. GPT-5.2 (xhigh): 35.4
3. Kimi K2.5: 31.5
4. GLM 5: 30.5
5. Claude Opus 4.5: 28.4
6. GLM 4.7: 24.8

#### Agentic (HLE w/ Tools)
1. Kimi K2.5: 51.8
2. GLM 5: 50.4
3. Gemini 3 Pro*: 45.8
4. GPT-5.2*: 45.5
5. Claude Opus 4.5*: 43.4
6. GLM 4.7: 42.8

#### Coding (SWE-bench Verified)
1. Claude Opus 4.5: 80.9
2. Kimi K2.5: 76.8
3. GLM 5: 77.8
4. DeepSeek-V3.2: 73.1
5. GLM 4.7: 73.8
6. Gemini 3 Pro: 76.2
7. GPT-5.2 (xhigh): 80.0

## Kimi K2.5 Overview

### Key Stats
- **Parameters**: 1T total / 32B active (MoE)
- **Context Window**: 256K tokens
- **Architecture**: 384 experts, 8 selected per token
- **Training**: ~15T tokens

### Performance Highlights
- **GDPval-AA Elo**: 1309 (best open-weights model)
- **Agentic Performance**: Behind only OpenAI and Anthropic models
- **Multimodal**: First flagship open model with native image/video input
- **MMMU Pro**: 75% (comparable to GPT-5.2 and Claude Opus 4.5)
- **AA-Omniscience Index**: -11 (low hallucination rate: 64%)

### vs GLM 4.7
- Context: 256K vs 200K
- Agent Swarm: Up to 100 sub-agents
- Thinking Mode: Unified reasoning model
- Native multimodality: Yes (first for open model)

## MiniMax Models

### MiniMax M2.1
- **SWE-bench Verified**: 74.0%
- **SWE-bench Multilingual**: 72.5%
- **Performance**: Competes with Kimi K2 Thinking, DeepSeek 3.2, and GLM 4.7
- **Artificial Analysis Intelligence Index**: 24 (below average)

## Code Quality Analysis (SonarSource)

| Metric | Claude Opus 4.5 Thinking | Gemini 3 Pro | GPT-5.2 High |
|--------|---------------------------|---------------|----------------|
| Pass Rate | 83.62% | 81.72% | 80.66% |
| Code Volume (LOC) | 639,465 | Low (efficient) | 974,379 |
| Concurrency Issues/MLOC | 133 | 69 | 470 |
| Resource Leaks/MLOC | 84 | 79 | 86 |
| Blocker Vulnerabilities/MLOC | 44 | 66 | 16 (best) |
| Generic Smells/MLOC | 2,225 | 3,044 | 3,453 |

**Key Findings:**
- **GPT-5.2 High**: Best security posture, but worst code verbosity and concurrency issues
- **Gemini 3 Pro**: Most efficient (lowest verbosity), but highest control flow errors
- **Claude Opus 4.5**: Best functional performance, high verbosity but reasonable complexity

## Summary Rankings

| Category | #1 | #2 | #3 |
|-----------|-----|-----|-----|
| Overall Intelligence | Gemini 3 Pro | GPT-5.2 High | Kimi K2.5 |
| Agentic Tasks | Kimi K2.5 | GLM 5 | Claude Opus 4.5 |
| Coding Quality | Claude Opus 4.5 | GLM 5 | Kimi K2.5 |
| Security | GPT-5.2 High | GLM 5 | Claude Opus 4.5 |
| Cost Efficiency | GLM 4.7 | DeepSeek V3.2 | MiniMax M2.1 |
| Long Context | Kimi K2.5 (256K) | GLM 4.7 (200K) | GLM 5 (200K+ DSA) |

**GLM 5 is the most improved** from GLM 4.7, closing the gap with frontier models in coding and agentic tasks while remaining significantly cheaper than proprietary alternatives.

## See Also
- [[DeepSeek Sparse Attention (DSA)|DeepSeek Sparse Attention (DSA).md]] - DSA architecture used in GLM 5

## Citations

- [[GLM-5 Hugging Face|https://huggingface.co/zai-org/GLM-5]] - Official GLM-5 model card and benchmarks
- [[GLM-5 vs GLM-4.7 Benchmarks|https://wavespeed.ai/blog/posts/blog-glm-5-vs-glm-4-7-upgrade-benchmarks]] - WaveSpeedAI comparison
- [[GIGAZINE GLM-5 Article|https://gigazine.net/gsc_news/en/20260212-z-ai-glm-5/]] - GLM-5 announcement and benchmarks
- [[Kimi K2.5 Comparison|https://kimi-k25.com/blog/kimi-k2-5-vs-glm-4-7]] - Kimi K2.5 vs GLM 4.7
- [[Artificial Analysis Kimi K2.5|https://artificialanalysis.ai/articles/kimi-k2.5-everything-you-need-to-know]] - Detailed Kimi K2.5 analysis
- [[SonarSource Code Quality|https://www.sonarsource.com/blog/new-data-on-code-quality-gpt-5-2-high-opus-4-5-gemini-3-and-more/]] - Code quality comparison
- [[Composio Model Comparison|https://composio.dev/blog/claude-4-5-opus-vs-gemini-3-pro-vs-gpt-5-codex-max-the-sota-coding-model]] - Real-world coding agent comparison
