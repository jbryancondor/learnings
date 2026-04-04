---
source: https://learnprompting.org/docs/basics/few_shot
date_accessed: 2026-04-04
published: 2024-01-01
author: Learn Prompting Contributors
company: Community
level_mapping: [Foundation]
tags: [in-context-learning, prompting-technique, examples, few-shot, zero-shot]
agent: agent-5
---

## Summary
Zero-shot prompting instructs a model to perform a task without examples, relying on the model's pre-trained knowledge. Few-shot prompting provides a small number of examples (demonstrations) within the prompt to guide the model to better performance through in-context learning. Both are techniques for steering LLM behavior without retraining.

## Key Concepts
- **Zero-Shot**: Task instruction without examples; leverages generalized pre-training
- **Few-Shot**: 2–5 task examples embedded in prompt to guide output format and quality
- **In-Context Learning**: Ability to learn from prompt examples without parameter updates
- **One-Shot**: Single example provided (midpoint between zero and few-shot)
- **Demonstration Format**: Examples show input-output pairs that define desired behavior
- **Format Adherence**: Few-shot helps models follow specific output patterns and structures
- **Scaling with Examples**: Performance typically improves as more examples are added (until a saturation point)

## Quotes / Evidence
"Zero-shot prompting means that the prompt used to interact with the model won't contain examples or demonstrations. The model is expected to solve a task without any examples, instead leveraging its pre-trained, general knowledge." — Learn Prompting

"Few-shot prompting is a technique that enables in-context learning where demonstrations serve as conditioning for subsequent examples where the model generates a response." — Prompt engineering consensus

## Related Terms
- Prompt Engineering
- Context Engineering
- Chain-of-Thought
- System Prompts
- Fine-Tuning vs. Prompting

## Relevance to Generative AI Engineer Role
Few-shot prompting is a practical technique you'll use frequently to improve output quality without fine-tuning. It's particularly valuable for format enforcement, code generation, and specialized tasks. Understanding when to use zero-shot (faster, simpler) vs. few-shot (higher quality, more context) informs your design decisions. As context windows grow, few-shot becomes more cost-effective than fine-tuning.

Sources:
- [Learn Prompting: Few-Shot](https://learnprompting.org/docs/basics/few_shot)
- [Prompt Engineering Guide: Zero-Shot](https://www.promptingguide.ai/techniques/zeroshot)
- [IBM: Zero-Shot Prompting](https://www.ibm.com/think/topics/zero-shot-prompting)
