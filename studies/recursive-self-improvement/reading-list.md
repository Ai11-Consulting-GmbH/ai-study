# Annotated reading list

[Study guide](README.md) · [Framework comparison](frameworks.md) · [Hypothetical experiment](experiment-design.md)

Primary sources checked on **24 October 2026**. These are links and original study notes; the papers and documentation are not reproduced. Repository implementation details can change after this date.

| Suggested order | Source | Focus while reading |
| --- | --- | --- |
| 1 | [Google codelab: agent evaluation and the self-evolving loop](https://codelabs.developers.google.com/codelabs/table-for-n/instructions) | Metric design, train/holdout separation, proxy failures and deployment boundaries |
| 2 | [GEPA repository](https://github.com/gepa-ai/gepa) | Reflective optimization and feedback-driven candidate proposals |
| 3 | [GEPA optimize_anything API](https://gepa-ai.github.io/gepa/api/optimize_anything/optimize_anything/) | Evaluator interface, validation versus test data, candidate representation and budgets |
| 4 | [Google ADK optimization](https://adk.dev/optimize/) | Sampler/optimizer separation and the scope of the experimental Python optimizers |
| 5 | [DREAM-RSI paper](https://arxiv.org/abs/2609.14858) | Online discovery, offline policy search and what the replay objective actually measures |
| 6 | [DREAM-RSI project](https://www.dream-rsi.com/) and [official repository](https://github.com/google-research/dream-rsi) | Recorded search trees, replay limits and research implementation |
| 7 | [ReasoningBank Google Research article](https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/) | Extracting and retrieving lessons from success and failure |
| 8 | [ReasoningBank paper](https://arxiv.org/abs/2509.25140) and [official repository](https://github.com/google-research/reasoning-bank) | Memory and self-judgment assumptions; distinguish these from model training |
| 9 | [AlphaEvolve DeepMind introduction](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/) | Candidate code generation with executable evaluators |
| 10 | [AlphaEvolve availability announcement](https://cloud.google.com/blog/products/ai-machine-learning/alphaevolve-is-available-for-everyone/) and [official client](https://github.com/Google-Cloud-AI/alphaevolve-on-googlecloud) | Managed-service architecture and the boundary between generation and evaluation |

## Discussion exercises

1. Design a rubric for document question answering that distinguishes unsupported claims, incomplete answers and justified abstention.
2. Construct a case where a longer instruction improves behavior but displaces the evidence needed to answer correctly. Specify how to detect that tradeoff.
3. Identify a document family that would leak across a random train/test split. Propose a better grouping rule.
4. Describe what can and cannot be learned by replaying a fixed experiment history.
5. Choose one failure that calls for a prompt change, one that calls for better evidence, and one that calls for additional real-world information.

## Before turning the study into implementation

Pin framework versions and inspect their current interfaces, dependencies and licenses. Define the permitted data flow for every model role. Establish the baseline, reviewer method, datasets, candidate surface and experiment budget before running optimization. Keep implementation proposals separate from measured results and report failed trials alongside successful ones.
