---
source: https://arxiv.org/abs/2201.11903
date_accessed: 2026-04-04
published: 2022-01-27
author: Wei et al.
company: Google Research
level_mapping: [Level 5 - MCP & Skills]
tags: [chain-of-thought, reasoning, prompting-technique, step-by-step, problem-solving]
agent: agent-5
---

## Summary
Chain-of-Thought (CoT) is a prompt engineering technique that enhances LLM reasoning by asking the model to show its work step-by-step. By providing few-shot examples where reasoning steps are explicitly shown, or by prompting "Let me think step by step," CoT enables models to solve complex problems through intermediate reasoning steps. CoT has become foundational for any complex, multi-step reasoning task.

## Key Concepts
- **Intermediate Reasoning**: Model verbalizes thought steps between input and output
- **Few-Shot CoT**: Providing examples with explicit reasoning steps
- **Self-Generated CoT**: Prompting model to generate reasoning on its own (sometimes called "Zero-Shot CoT")
- **Step Decomposition**: Breaking complex tasks into manageable subtasks
- **Error Visibility**: Explicit reasoning makes failures easier to identify and debug
- **Performance Boost**: CoT significantly improves performance on math, logic, and commonsense tasks
- **Multimodal Extensions**: 2024 research extended CoT to combine text and visual reasoning
- **Reasoning Tokens**: In OpenAI's o1 models, reasoning steps are explicitly generated with token budget

## Quotes / Evidence
"Chain of thought prompting significantly enhances reasoning capabilities of LLMs, making them more adept at solving complex tasks like math problems, commonsense reasoning, and symbolic manipulation." — Industry consensus

"By providing examples where the reasoning process is explicitly shown, the LLM learns to include reasoning steps in its responses." — Prompting best practice

"CoT mirroring human-like reasoning processes makes it possible to understand and debug the model's thinking when it goes wrong." — Practical benefit

## Related Terms
- Prompt Engineering
- ReAct Pattern
- Tree of Thought
- Few-Shot Prompting
- Agent Framework

## Relevance to Generative AI Engineer Role
CoT is fundamental to working with LLMs on anything complex. You'll use CoT to improve reliability on reasoning tasks, debug agent failures, and design prompts that expose intermediate thinking. In production systems, you'll monitor whether agents are showing their reasoning—low-quality CoT often precedes errors.

Sources:
- [Original CoT Paper - arXiv 2022](https://arxiv.org/abs/2201.11903)
- [IBM: Chain of Thought Prompting](https://www.ibm.com/think/topics/chain-of-thoughts)
- [Prompt Engineering Guide: CoT](https://www.promptingguide.ai/techniques/cot)
