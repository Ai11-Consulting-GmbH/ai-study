# A hypothetical document question answering experiment

[Study guide](README.md) · [Framework comparison](frameworks.md) · [Reading list](reading-list.md)

This is an educational exercise created for these study materials. It describes no organization, deployed system, private dataset or measured result.

## Task

An assistant answers questions using short synthetic fact sheets about imaginary museums. Each sheet gives opening hours, available facilities and admission conditions. The assistant should answer using the supplied information and state when the sheet does not provide the answer.

For example, an invented sheet might say that the Cedar Museum opens at 10:00 on Saturdays and provides bicycle parking. A question about Saturday opening time has an answer; a question about wheelchair access does not. Bicycle parking is not evidence of accessibility facilities.

The study question is whether a revised instruction improves correctness and completeness while preserving justified abstention.

## Prepare the examples

Create synthetic fact sheets and questions with answerable, partially answerable and unanswerable cases. Include distractors and conflicting versions when the task specifies which version takes precedence. Record required facts, prohibited unsupported claims and the relevant source spans before evaluating candidates.

Separate development, validation and final-test sets by museum and document template. Changing a museum's name is not enough to make a near-duplicate example an independent test. Keep final-test questions, answer keys and case-level feedback outside the optimization process.

## Freeze the comparison

| Component | Experimental choice |
| --- | --- |
| Baseline | A fixed instruction and output format |
| Candidate surface | Instruction text only |
| Model | Same model identity and settings for baseline and candidates |
| Inputs | Same fact sheets and questions within each paired comparison |
| Budget | Predeclared candidate count, evaluation calls and runtime |
| Scoring | Fixed correctness and completeness rubric with failure accounting |

Use a simple example batch to check that the scorer distinguishes correct, partially correct, unsupported and failed answers. This check evaluates the measurement procedure before any optimizer is allowed to target it.

## Define the feedback

An evaluator should return a score plus a concrete explanation. For instance: the answer supplied an accessibility claim that the sheet does not contain, or it omitted the opening time that the question explicitly requested.

Exact facts such as times can support deterministic checks, but the evaluator must still account for negation, conditions and alternative valid wording. Use subject-matter review when the rubric involves semantic judgments. Keep any model-based judge separate from the candidate instruction and calibrate it against reviewed examples.

Record these dimensions separately:

- Correctness of requested facts.
- Completeness of answerable portions of the question.
- Unsupported factual claims.
- Appropriate treatment of missing information.
- Completed, failed and missing attempts.
- Latency and resource use.

Do not treat every abstention as a failure or let abstaining on every question produce a winning score. Do not exclude failed attempts from the reported outcome denominator.

## Run a bounded search

1. Evaluate the frozen baseline.
2. Use development failures to propose candidate instructions.
3. Run candidates under the same conditions and select using validation results.
4. Stop at the declared budget or when the no-progress condition is met.
5. Freeze a finalist and evaluate it on the separate final-test set.
6. Report improvements, regressions, failures and uncertainty; retain the baseline if the finalist does not satisfy the criteria.

GEPA is one possible optimizer for this exercise because its interface accepts a candidate and a task-specific evaluator. The experiment can also be conducted manually to study the evaluation design before adding automation. [GEPA API](https://gepa-ai.github.io/gepa/api/optimize_anything/optimize_anything/)

## Interpret the result

A better validation score is a selection result. Evidence of generalization comes from the separate final test, subject to its size and representativeness. Repeat paired runs if output variability could change the conclusion. If final-test findings guide a new round of tuning, obtain a fresh sealed test set for the next generalization claim.

No numerical outcome is assumed for this exercise. A useful result may be an improved instruction, a finding that the model lacks the required capability, or a discovery that the evaluator needs a better definition of correctness. Revise an inadequate evaluator as a separately versioned measurement change, then re-establish the baseline rather than comparing incompatible scores.
