# Contributing to AI Study

Help readers understand a method, evaluate its evidence or design a better experiment. Contributions can correct a source, improve an explanation, add an exercise or introduce a new study grounded in public material.

## Suggest a change

Use a [source correction](https://github.com/Ai11-Consulting-GmbH/ai-study/issues/new?template=source-correction.yml) for an inaccurate claim, broken link or changed API. Use a [study suggestion](https://github.com/Ai11-Consulting-GmbH/ai-study/issues/new?template=study-suggestion.yml) for a new topic. Include the relevant page and primary sources so others can assess the suggestion.

For a direct edit, open a pull request explaining the reader-facing change and how it was checked. Keep unrelated edits separate. A documentation correction usually needs a careful source and link review rather than a new test suite.

## Write a study

1. Create a descriptive directory under `studies/`, using lowercase words separated by hyphens.
2. Start from the [study template](templates/study-template.md).
3. Explain the central concept before discussing implementation details.
4. Link claims to papers, official documentation or maintained project repositories.
5. State the date on which sources were checked and separate documented facts from interpretations or proposed experiments.
6. Add the study to the catalog in the [repository README](README.md).

Use relative links for repository documents. Give readers a clear route back to the study guide. Small tables and Mermaid diagrams are useful when they explain a comparison or process more clearly than prose.

## Evidence and examples

Preserve the scope of each source. A benchmark on one task does not establish a gain on another task. Attribute published numbers to their authors, keep limitations near the claim they qualify, and identify hypothetical examples explicitly.

Prefer summaries and links to copying source material. If a code sample is included, distinguish executed examples from pseudocode and specify versions needed to reproduce it. Do not imply that code was tested when it was only inspected.

Use public sources and fictional examples. Do not include confidential organization or product details, customer data, credentials, private repository links, internal identifiers or unpublished measurements.

## Before submitting

- Read the change as a learner who has not seen the surrounding discussion.
- Check citations, dates, relative links, tables and code fences.
- Confirm that claims and examples match their stated evidence.
- Check the patch and added files for non-public information.
- Run `git diff --check` to catch whitespace errors.

Keep contributions focused on learning value. Avoid unsupported claims of superiority, fabricated results or promises about future framework behavior.
