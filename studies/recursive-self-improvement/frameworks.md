# Framework comparison

[Study guide](README.md) · [Hypothetical experiment](experiment-design.md) · [Reading list](reading-list.md)

Research checked: **24 October 2026**. The descriptions below summarize publicly documented behavior. Suggested use cases are educational interpretations, not measured comparisons between frameworks.

| Framework | Optimization target | Feedback used | Potential use case |
| --- | --- | --- | --- |
| DREAM-RSI | Exploration policy | Recorded discovery trees and replay scores | Allocate effort in repeated discovery tasks |
| GEPA | Prompts or other text-defined artifacts | Evaluation scores plus diagnostic feedback | Optimize instructions against a task-specific evaluator |
| Google ADK optimization | Agent instructions; selected optimizer variants also cover skill instructions | ADK evaluation results | Experiment within an ADK agent workflow |
| ReasoningBank | Experience memory | Success/failure trajectories and self-judgment | Retrieve reusable lessons for later tasks |
| AlphaEvolve | Candidate programs | Executable evaluators | Search for improved algorithms |

## Google DREAM-RSI

DREAM-RSI alternates online discovery with offline policy search. Online attempts produce a tree of candidate solutions. Offline search replays alternative exploration policies on recorded trees and retains the best policy for the next discovery round. The policy controls how the agent allocates its search budget; the discovery model, evaluator and task stay fixed. [Official repository](https://github.com/google-research/dream-rsi)

Replay can use outcomes already present in the history. It cannot supply the outcome of an unexecuted candidate or an unseen task. A policy that improves the historical replay objective is not guaranteed to improve future task performance. Descriptions of replay with no new executions do not eliminate policy-generation costs or the online discovery phase. [Paper](https://arxiv.org/abs/2609.14858), [project explanation](https://www.dream-rsi.com/)

The repository is research code and explicitly disclaims production readiness. Its registered agents include Gemini, Claude and Codex. Compatibility with a different agent or inference service requires checking the available adapters. [Agent implementations](https://github.com/google-research/dream-rsi/tree/main/dream_rsi/agents)

This approach is worth studying when repeated discovery creates enough history to compare experiment-selection policies.

## GEPA

GEPA uses reflective feedback to propose changes to candidate artifacts. Its general API accepts a candidate, an evaluator and optional development, validation and test examples. Evaluation feedback can include a score and diagnostic information explaining the failure. [Current API](https://gepa-ai.github.io/gepa/api/optimize_anything/optimize_anything/)

A hypothetical integration supplies an evaluator that runs a candidate instruction on a task and returns both its score and a useful failure explanation. The integration must define its own task, data boundary and scoring rules. No particular application runtime or inference provider is assumed here.

Pin a package version before writing runnable examples. Current documentation and older examples use different configuration names and budget fields. This study therefore specifies experiment behavior rather than presenting an untested installation recipe. [Repository](https://github.com/gepa-ai/gepa)

## Google ADK optimization

ADK exposes evaluation-driven optimization through `adk optimize`. Its GEPA root-prompt optimizer changes root instructions; a separate root-agent optimizer can also change instructions of supplied skills. The feature is documented for ADK Python, and the GEPA optimizers are experimental. Do not infer feature parity across all ADK language SDKs or automatic optimization of tools and sub-agents. [Optimization documentation](https://adk.dev/optimize/)

Google also provides a hands-on evaluation and self-evolving-loop tutorial. It is useful for studying metric design and separation of optimization from deployment. [Codelab](https://codelabs.developers.google.com/codelabs/table-for-n/instructions)

ADK is useful for studying optimization within its agent framework. GEPA can also be evaluated separately when a different runtime already supplies an appropriate evaluator.

## Google ReasoningBank

ReasoningBank extracts structured lessons from successful and failed trajectories and retrieves relevant memories for subsequent tasks. The published method uses model self-judgment and appends extracted memories. It learns through memory rather than changing model weights. Reported evaluations concern browsing and software-engineering tasks. [Google Research explanation](https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/)

Applications of experience memory need to consider provenance, scope, expiry, correction and removal; these should not be assumed to come from the original method. An incorrect self-assessment can propagate into later tasks if it is retained without correction. The repository describes a research demonstration. [Official repository](https://github.com/google-research/reasoning-bank)

## Google AlphaEvolve

AlphaEvolve generates and evolves programs against a supplied evaluator. This is suitable when candidate quality can be measured by executing the program. [DeepMind introduction](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)

It became generally available on Google Cloud on 9 July 2026. Its public client is not the full service running locally: generation runs in Google Cloud, while evaluation can run locally. Access, data flow, models and pricing should be checked again before adoption. [Availability announcement](https://cloud.google.com/blog/products/ai-machine-learning/alphaevolve-is-available-for-everyone/), [official client](https://github.com/Google-Cloud-AI/alphaevolve-on-googlecloud)

Suitable educational exercises include optimizing a scheduling heuristic or numerical algorithm against a fixed evaluator. Establish that the evaluator measures the intended objective before expanding the search space.

## Selection principle

Choose the method according to the artifact being improved and the feedback available. A framework cannot compensate for weak labels, unrepresentative examples or an evaluator that rewards the wrong behavior. Authors' benchmark improvements should not be treated as guaranteed gains on another task.
