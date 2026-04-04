---
source: https://martinfowler.com/articles/function-call-LLM.html
date_accessed: 2026-04-04
published: 2024-01-01
author: Martin Fowler & Community
company: Thoughtworks
level_mapping: [Level 5 - MCP & Skills]
tags: [tool-use, function-calling, external-actions, agent-capability, structured-output]
agent: agent-5
---

## Summary
Tool use (function calling) enables LLMs to take actions beyond text generation by calling external functions, APIs, and tools. The LLM identifies the appropriate tool, extracts parameters from natural language, and returns structured JSON. The actual function call happens outside the model; the LLM suggests what to call. This is the foundation of agentic systems, enabling models to interact with databases, file systems, calculators, search engines, and domain-specific tools.

## Key Concepts
- **Function Calling**: LLM identifies function to call and extracts parameters from natural language
- **Structured Output**: Model returns JSON with function name and arguments
- **External Execution**: System (not model) actually executes the function
- **Feedback Loop**: Function results returned to LLM for next action planning
- **Tool Definition**: Clear function signatures and descriptions guide model behavior
- **Error Handling**: Model can reason about API errors and retry
- **Real-World Actions**: Enables agents to read/write files, query databases, send emails, etc.
- **Agent Foundation**: Essential for agentic AI systems (ReAct, autonomous agents)

## Quotes / Evidence
"Function calling enables LLMs to go beyond simple text generation by interacting with external tools and real-world applications." — Industry consensus

"The LLM does not call the tools directly. Instead, it suggests the tool to call. The user then calls the tool separately and provides results back to the LLM." — How tool use works

"Since tool calling is central to agentic workflows, models should be evaluated by how well they perform in function calling." — 2024-2025 evaluation priority

## Related Terms
- ReAct Pattern
- Agent Framework
- MCP (Model Context Protocol)
- Chain-of-Thought
- Autonomous Development Loop

## Relevance to Generative AI Engineer Role
Tool use is fundamental to agentic systems. You'll design tool definitions, manage API integrations, implement error handling, and evaluate how well models call tools. Understanding function-calling performance directly impacts agent reliability. Tools are your interface between model reasoning and real-world action.

Sources:
- [Martin Fowler: Function Call LLM](https://martinfowler.com/articles/function-call-LLM.html)
- [OpenAI: Function Calling Guide](https://community.openai.com/t/prompting-best-practices-for-tool-use-function-calling/1123036)
- [Prompt Engineering Guide: Function Calling](https://www.promptingguide.ai/agents/function-calling)
