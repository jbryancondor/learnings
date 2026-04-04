---
source: https://www.mckinsey.com/featured-insights/mckinsey-explainers/what-is-a-context-window
date_accessed: 2026-04-04
published: 2024-01-01
author: McKinsey
company: McKinsey & Company
level_mapping: [Foundation]
tags: [context-window, memory, LLM-capability, inference]
agent: agent-5
---

## Summary
The context window (or context length) of a large language model is the amount of text, measured in tokens, that the model can consider simultaneously during inference. It functions as the model's short-term working memory. Context windows have grown exponentially from 512 tokens in 2018 to 10+ million tokens in 2025, but practical effectiveness often caps around 30–60% of advertised length.

## Key Concepts
- **Context Window**: The number of tokens an LLM can process at once
- **Token Capacity**: Maximum input + output tokens allowed in a single inference call
- **Effective Context**: The portion of context window where the model maintains high accuracy (typically 30–60% of advertised window)
- **Context Length Evolution**: GPT-3.5 (4K tokens) → GPT-4 (8K) → GPT-4 Turbo (128K) → GPT-4o (128K)
- **Lost-in-the-Middle Effect**: Models struggle to access information in the middle of very long contexts
- **Scaling Implications**: Larger windows enable multi-document analysis, full-codebase understanding, and many-shot learning

## Quotes / Evidence
"Context windows are like a human's short-term memory—like us, LLMs can only 'look' at so much information simultaneously." — McKinsey & Company

"The exponential growth from 512-token windows in 2018 to 10-million-token windows in 2025 traces a decade-long transformation. What was impossible—processing entire codebases, analyzing complete conversations, performing many-shot in-context learning—has become routine." — Industry analysis

## Related Terms
- Tokenization & Token Budget
- Embeddings
- RAG (Retrieval-Augmented Generation)
- Long Context Reasoning
- Context Engineering

## Relevance to Generative AI Engineer Role
Context window management is foundational to your role. You'll need to understand your chosen model's context limits, optimize how you pack information into prompts, and design retrieval strategies for data that exceeds context length. Larger context windows enable richer interactions but increase latency and cost. Strategic use of context engineering amplifies what's possible within those bounds.

Sources:
- [What is a context window - McKinsey](https://www.mckinsey.com/featured-insights/mckinsey-explainers/what-is-a-context-window)
- [Context Window LLM Comparison 2025](https://aiagentmemory.org/articles/context-window-llm-comparison-2025/)
- [IBM Context Window Explanation](https://www.ibm.com/think/topics/context-window)
