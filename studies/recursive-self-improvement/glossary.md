# Glossary

[Study guide](README.md) · [Framework comparison](frameworks.md) · [Practice exercise](experiment-design.md) · [Primary sources](reading-list.md)

These working definitions describe how terms are used in this study. Related papers may use them more narrowly or broadly.

| Term | Meaning in this study |
| --- | --- |
| Agent | A system that uses a model to choose actions or steps toward a task, often with tools and state |
| Candidate | A proposed prompt, program, workflow or policy being evaluated |
| Incumbent | The current accepted version against which candidates are compared |
| Evaluator | The procedure that turns observed task outcomes into scores and diagnostic feedback |
| Rubric | The criteria used to judge an answer or behavior |
| Development set | Examples available for failure analysis and candidate generation |
| Validation set | Examples used to select candidates or tune decisions; this feedback participates in optimization |
| Final test set | A separate set evaluated after a candidate is frozen and kept outside its selection process |
| Data leakage | Information from an evaluation set influencing learning or selection in a way that weakens the claimed independence of the result |
| Reflection | Analysis of outcomes and feedback to propose a revision; reflection alone does not establish that the revision is better |
| Prompt optimization | Searching over instructions or other prompt content while holding model parameters fixed |
| Experience memory | Stored lessons or representations from previous tasks that are retrieved for later tasks |
| Exploration policy | A strategy for allocating attempts, refinement and stopping decisions during search |
| Replay | Evaluating a policy against recorded outcomes; replay cannot provide outcomes that were never recorded |
| Grounding | Support for a claim in the allowed source material; citing an existing source does not by itself prove support |
| Abstention | Declining to provide a claim or answer when the available information is insufficient |
| Proxy metric | A measurable substitute for the desired outcome that may omit important aspects of quality |
| Reward hacking | Improving the measured objective by behavior that fails the intended objective |
| Paired comparison | Comparing candidates on the same cases under comparable conditions |
| Promotion | Accepting a tested candidate as the next incumbent under predeclared criteria |
| Recursive self-improvement | A system improving its own capabilities or the process used to produce further improvements; distinguish this from revising a single answer or routinely tuning an application |

For the specific mechanisms behind these terms, see the [DREAM-RSI paper](https://arxiv.org/abs/2609.14858), [GEPA API](https://gepa-ai.github.io/gepa/api/optimize_anything/optimize_anything/), and [ReasoningBank explanation](https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/). The [Google evaluation codelab](https://codelabs.developers.google.com/codelabs/table-for-n/instructions) provides a practical discussion of metrics and optimization behavior.
