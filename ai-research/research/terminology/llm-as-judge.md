---
source: https://www.evidentlyai.com/llm-guide/llm-as-a-judge
date_accessed: 2026-04-04
published: 2024-01-01
author: Evidently AI & Research Community
company: Evidently
level_mapping: [Level 6 - Harness Engineering]
tags: [evaluation, judging, scoring, automated-assessment, quality-control]
agent: agent-5
---

## Summary
LLM-as-a-Judge is a framework that uses capable LLMs as automated evaluators to assess outputs from other AI systems. Instead of relying on human reviewers or heuristic metrics, you provide a judge model with criteria, the AI output, and ask it to score and reason about quality. LLM judges achieve 80-90% agreement with human reviewers on many dimensions and scale evaluation far beyond manual review. This is foundational for evaluation-over-review workflows.

## Key Concepts
- **Judge Model**: A capable LLM that evaluates other outputs
- **Evaluation Rubric**: Explicit criteria and scoring instructions
- **Reasoning Output**: Judge explains reasoning, not just scores
- **Pairwise Comparison**: Judge compares two outputs and identifies the better one
- **Pointwise Scoring**: Judge assigns scores on a scale (1-10, etc.)
- **Reference-Guided**: Judge compares against a reference solution
- **Automated Scaling**: Evaluation at the speed of inference, not human review
- **Bias Mitigation**: Systematic evaluation reduces personal reviewer bias

## Quotes / Evidence
"LLM-as-a-Judge employs large language models as evaluators to assess AI system outputs based on custom criteria defined in an evaluation prompt." — Industry definition

"Strong LLM judges achieve 80-90% agreement with human evaluators on many quality dimensions, comparable to inter-annotator agreement between humans." — Validation data

"LLM-as-a-Judge is scalable and reproducible, significantly reducing costs and time compared to human evaluation." — Practical benefit

## Related Terms
- Evaluation Over Review
- Harness Engineering
- LLM as Judge
- Quality Metrics
- Automated Testing

## Relevance to Generative AI Engineer Role
LLM-as-Judge is your primary mechanism for evaluating agent outputs at scale. You'll define evaluation rubrics, select judge models, implement scoring pipelines, and use judge feedback to improve systems. Automated judging enables rapid iteration on AI systems without human bottlenecks.

Sources:
- [Evidently: LLM-as-Judge Guide](https://www.evidentlyai.com/llm-guide/llm-as-a-judge)
- [arXiv: Survey on LLM-as-Judge](https://arxiv.org/abs/2411.15594)
- [Langfuse: LLM-as-Judge](https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge)
