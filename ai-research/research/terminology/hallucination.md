---
source: https://lilianweng.github.io/posts/2024-07-07-hallucination/
date_accessed: 2026-04-04
published: 2024-07-07
author: Lilian Weng
company: OpenAI
level_mapping: [Foundation]
tags: [hallucination, factuality, grounding, reliability, LLM-limitations]
agent: agent-5
---

## Summary
Hallucination (also called confabulation or delusion) is the generation of fluent, syntactically correct but factually inaccurate or unsupported content by LLMs. The model produces plausible-sounding text that is not grounded in its training data or provided context. Hallucinations are an inherent limitation of LLMs related to how they generate tokens probabilistically rather than retrieving facts.

## Key Concepts
- **Hallucination**: Generation of false or unsupported information presented as fact
- **Intrinsic Hallucination**: Information contradicts the provided context
- **Extrinsic Hallucination**: Information is not supported by the provided context but may be factually true
- **Confabulation**: Erroneous construction of responses without perceptual grounding
- **Factual Inaccuracy**: Deviation from verifiable truth in training data or external sources
- **Token Prediction Errors**: Hallucinations arise from probabilistic next-token selection, not retrieval

## Quotes / Evidence
"Hallucination refers to the generation of content by LLMs that is fluent and syntactically correct, but factually inaccurate or unsupported by external evidence." — Lilian Weng, July 2024

"Hallucination is an inevitable feature of Large Language Models due to their core design: they predict the most probable next token, not retrieve facts." — Recent arXiv research

## Related Terms
- Grounding
- RAG (Retrieval-Augmented Generation)
- Fact-Checking
- System Prompts
- Context Engineering

## Relevance to Generative AI Engineer Role
Hallucination is your primary reliability challenge. You'll need to implement grounding strategies (RAG, retrieval), verification pipelines, and evaluation metrics to detect and mitigate false outputs. In production systems, unchecked hallucinations can destroy user trust and create legal liability. Designing for factuality is essential.

Sources:
- [Extrinsic Hallucinations in LLMs - Lil'Log](https://lilianweng.github.io/posts/2024-07-07-hallucination/)
- [Large Language Models Hallucination Survey](https://arxiv.org/html/2510.06265v2)
- [IBM: AI Hallucinations](https://www.ibm.com/think/topics/ai-hallucinations)
