# GLM-4.5 and GLM-4.5-Air Summary (2025)

## Overview
GLM-4.5 and GLM-4.5-Air are advanced open-source AI models by Zhipu AI (Z.ai), with strengths in reasoning, coding, and agentic workflows [1][2].

- **GLM-4.5 (Full):** 355B parameters, 32B active per query.
- **GLM-4.5-Air:** 106B parameters, 12B active.
- MoE architecture; Thinking and Non-Thinking modes for agentic or rapid tasks.

## Pricing & Availability
- API access via Z.ai, OpenRouter, SiliconFlow, and more.
- Pricing: GLM-4.5 ~$0.11–$0.48 per million input tokens, GLM-4.5-Air ~$0.16 per million input tokens [3][4].
- Z.ai offers $3/mo (Lite, ~120 prompts/5hrs) and $15/mo (Pro) plans for coding agents [5][6].
- Fully open weight models available under MIT license.

## Hardware & Hosting
- **GLM-4.5:** Needs 48–80 GB VRAM (A100/H100); 640 GB VRAM (8x H100) for max context/vision tasks.
- **GLM-4.5-Air:** Runs on 16 GB VRAM (A40, 4090); INT4 quantization possible.
- **Cloud cost:** A100/H100 GPUs: $3–$15/hr; continuous use $2K–10K+/mo [7][8].
- Hosted API is often preferable for most users.

## Performance & Benchmarks
- **GLM-4.5:** #3 overall across AI benchmarks, #1 open weight [1][9].
- [ ] **GLM-4.5-Air:** #6 overall, leading for its size [10].
- Strong coding accuracy (SWE-bench, LiveCodeBench), tool-calling 90.6%.
- Large context: 128K tokens (full); 130K (Air).

## Features
- **Agent-native:** Advanced tool use, multi-turn workflows.
- **Fast inference:** Air model ~0.9s to first token.
- Both models much more cost-effective than most proprietary models.

## CLI Agent Compatibility
- Works out-of-the-box with Claude Code, Roo Code, OpenCode, Crush, Goose, and others. Authentication via Z.ai API key and endpoint config [5][6].
- One subscription enables use across multiple agents.

## Latency & Global Deployment
- Default API served from China. Latency from New Zealand 250–350ms [11].
- Lower latency: local or regional cloud/self-hosting possible (with sufficient GPU).

## Model Comparison Table

| Model                | Params | Context | Bench Rank | Tool Use   | Hosting        | Notes                                  |
|----------------------|--------|---------|------------|------------|--------------|----------------------------------------|
| GLM-4.5 (full)       | 355B   | 128K    | #3 Global  | 90.6%      | API/Self      | Best open source, heavy GPU required   |
| GLM-4.5-Air          | 106B   | 130K    | #6 Global  | 90.6%      | API/Self      | Fast, cheap, runs on smaller GPUs      |
| Claude 4 Opus        | ~70B   | 100K+   | Top-tier   | ~89.5%     | API only      | Proprietary, highest agentic/coding    |
| Claude 4 Sonnet      | ~70B   | 80K+    | High       | Slightly < | API only      | Good, but not open weight              |
| DeepSeek R1          | 180B   | 128K    | #2 OpenWgt | ~87%       | API/Self      | Competes with GLM-4.5 in Asia          |
| Qwen3-235B Thinking  | 235B   | Large   | #5 Global  | ~86%       | API/Self      | Strong coding, slower throughput       |
| Gemini 2.5 Pro       | NA     | Large   | Competitive| NA         | API only      | Proprietary, often more expensive      |

## Use Cases
- Coding assistants, multi-turn agent workflows, document analysis, multilingual tasks, rapid prototyping.
- Enterprise: self-host for privacy and customization.

## Drawbacks & Considerations
- May lack SLA/support like closed platforms.
- Large models need careful orchestration/devops.

---

## References


1. [GLM-4.5 Open-Source Model Deep Dive (C3 UNU)](https://c3.unu.edu/blog/glm-4-5-the-open-source-model-that-challenges-proprietary-ai-dominance)
2. [GLM-4.5: Reasoning, Coding, and Agentic Abililties (Zhipu AI/Z.ai)](https://z.ai/blog/glm-4.5)
3. [CometAPI GLM-4.5 Series Pricing Analysis](https://www.cometapi.com/how-much-does-glm-4-5-series-cost/)
4. [SiliconFlow GLM-4.5 Model Specs](https://www.siliconflow.com/models/zai-org-glm-4-5)
5. [GLM Coding Plan Details (Z.ai)](https://z.ai/subscribe)
6. [Claude Code and Agent Compatibility Discussion](https://www.reddit.com/r/ClaudeCode/comments/1n7qtyi/zai_launch_claude_code_glm_45glm_45air_coding/)
7. [Novita AI GLM-4.5 GPU Benchmark](https://blogs.novita.ai/glm-4-5v-vram-setup-choosing-the-right-gpu-for-multimodal-ai/)
8. [Hosting Strategies for LLMs in 2025](https://www.linkedin.com/pulse/navigating-open-source-frontier-choosing-hosting-large-jovan-njegic-np6le)
9. [Artificial Analysis GLM-4.5 Performance](https://artificialanalysis.ai/models/glm-4.5)
10. [InfoQ: GLM-4.5 Launches with Strong Reasoning, Coding, and Agentic Abilities](https://www.infoq.com/news/2025/08/glm-4-5/)
11. [VentureBeat: Z.ai Model Geography and Latency](https://venturebeat.com/ai/chinese-startup-z-ai-launches-powerful-open-source-glm-4-5-model-family-with-powerpoint-creation)
