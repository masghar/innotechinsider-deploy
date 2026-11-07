# Thinking Machines Lab Unveils Inkling 2 Small MoE with 17B Active Routing

> Thinking Machines Lab announced Inkling 2 Small, a 594-billion parameter MoE model that activates only 17 billion per token. Open weights drop next week.

By InnotechInsider Staff · New AI Models · Nov 5, 2026
Canonical URL: https://innotechinsider.com/ai-models/thinking-machines-lab-inkling-2-small-moe-open-weights/

> **TL;DR** Thinking Machines Lab has unveiled Inkling 2 Small, a 594-billion parameter mixture-of-experts model that routes down to 17 billion active parameters per token, with open weights slated for release next week following red-team evaluations.

San Francisco-based research collective Thinking Machines Lab took the wraps off Inkling 2 Small on Friday morning, introducing a sparse architecture designed to push parameter scale without multiplying operational compute costs. Despite carrying the "Small" moniker, the model spans 594 billion total parameters across its expert layers, but activates just 17 billion per token during forward inference.

The laboratory confirmed that it will publish the model’s base and instruction-tuned weights by mid-November, once external auditors conclude automated vulnerability sweeps and catastrophic risk benchmarks.

![computer science engineer inspecting high density server blade rack](https://images.unsplash.com/photo-1581092919535-7146ff1a590b?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxjb21wdXRlciUyMHNjaWVuY2UlMjBlbmdpbmVlciUyMGluc3BlY3RpbmclMjBoaWdoJTIwZGVuc2l0eSUyMHNlcnZlciUyMGJsYWRlJTIwcmFja3xlbnwwfDB8fHwxNzkzOTI1ODQ4fDA&ixlib=rb-4.1.0 "computer science engineer inspecting high density server blade rack — Photo by ThisisEngineering on Unsplash")

## Aggressive Sparsity at the Frontier

The core selling point of Inkling 2 Small is its extreme sparsity ratio. Traditional dense architectures calculate activations across every single parameter for every single token, making large-scale deployments notoriously expensive. Even popular [mixture of experts](https://en.wikipedia.org/wiki/Mixture_of_experts) implementations from recent years typically route between 15% and 25% of their total parameter mass.

Inkling 2 Small cuts that down to roughly 2.8%. By deploying 128 fine-grained experts per feed-forward block and routing tokens across only four at any given step, the system limits runtime arithmetic to that of a modest 17-billion-parameter network. According to technical documentation shared by the lab, the architecture leans on fine-grained auxiliary-loss-free load balancing to prevent specific experts from hogging execution bandwidth.

| Specification | Inkling 2 Small | DeepSeek-V3 | Llama 3.1 70B |
|---|---|---|---|
| **Architecture** | Sparse MoE | Sparse MoE | Dense Transformer |
| **Total Parameters** | 594 Billion | 671 Billion | 70 Billion |
| **Active Parameters** | 17 Billion | 37 Billion | 70 Billion |
| **Routing Granularity** | 4 of 128 experts | 8 of 256 experts | None (Dense) |
| **Context Window** | 128k tokens | 128k tokens | 128k tokens |
| **Weight Availability** | Open weights (Nov 2026) | Open weights | Open weights |

Thinking Machines Lab claims this layout allows the model to match the coding and complex mathematics throughput of significantly heavier dense architectures, while keeping per-token latency within margins familiar to teams deploying modern [ai apps](/ai-apps/) in production environments.

## The Memory Footprint Reality Check

Compute efficiency is only half of the modern deployment equation, however. While execution FLOPs scale strictly with the 17 billion active parameters, loading the model into memory requires hosting all 594 billion.

![close up macro shot of liquid cooling pipes running across ai accelerator chips](https://images.pexels.com/photos/11047218/pexels-photo-11047218.jpeg?auto=compress&cs=tinysrgb&fit=crop&h=627&w=1200 "close up macro shot of liquid cooling pipes running across ai accelerator chips — Photo by Vlad Samoylik on Pexels")

Unquantized at 16-bit precision, that translates to well over a terabyte of high-bandwidth memory simply to park the checkpoint. Even when packed into production-grade FP8 or aggressive experimental 4-bit formats, serving Inkling 2 Small demands high-density multi-GPU clusters. For the median enterprise team managing budgets across [biz it](/biz-it/), self-hosting the full unquantized weights will remain tethered to specialized infrastructure rather than off-the-shelf single-node servers.

Thinking Machines Lab stated that optimized quantized checkpoints will accompany the primary release to help mitigate this footprint. Independent hosting providers, including several inference-as-a-service platforms, have already signaled intention to spin up dedicated API endpoints as soon as the files hit public repositories.

## Safety Checkpoints Before the Public Drop

The delay between today's architectural announcement and next week’s artifact drop centers entirely on red-teaming. Thinking Machines Lab is subjecting the checkpoint to rigorous red-teaming runs aligned with guidance from the [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework), specifically testing for automated vulnerability exploitation, CBRN misuse queries, and unprompted agentic drift.

The team has opted for an unrestricted open-weights license, declining to impose compute-capping commercial clauses or telemetry obligations on downstream developers. If the remaining test batteries clear without incident, developers will be able to download the complete parameter weights directly from Hugging Face by November 13.

By delivering high-parameter reasoning within a sub-20-billion compute envelope, Thinking Machines Lab is making a clear bet: the future of deployable open intelligence belongs to the sparsest route possible.
