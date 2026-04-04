---
source: https://www.promptingguide.ai/techniques/react
date_accessed: 2026-04-04
published: 2023-10-01
author: Yao et al.
company: Google Research / Community
level_mapping: [Level 5 - MCP & Skills]
tags: [react-pattern, reasoning-acting, agent-pattern, tool-use, decision-making]
agent: agent-5
---

## Summary
The ReAct (Reasoning + Acting) pattern is an iterative framework for AI agents that combines chain-of-thought reasoning with tool use and action. Agents alternate between: (1) reasoning steps (thinking about the problem), (2) actions (using tools, APIs, or taking steps), and (3) observations (processing results). This cycle repeats until the agent reaches a conclusion. ReAct is especially effective for tasks involving ambiguity, exploration, or where the optimal path isn't immediately clear.

## Key Concepts
- **Thought Step**: Verbalized reasoning and planning
- **Action Step**: Using tools, making API calls, or taking steps in the environment
- **Observation Step**: Processing results and updating understanding
- **Adaptive Iteration**: Adjusting strategy based on observations
- **Tool Integration**: Predefined actions that agents can invoke
- **Environmental Interaction**: Real-time feedback from tool use informs next steps
- **Explicit Planning**: Unlike pure CoT, ReAct includes explicit action selection
- **Exploration Support**: Good for research, troubleshooting, and investigation

## Quotes / Evidence
"ReAct combines an LLM's chain of thought reasoning with external tool use, alternating between reasoning and taking actions, receiving observations from the environment." — IBM definition

"ReAct agents adapt to ambiguity and evolving requirements where the best path forward isn't clear. This makes ReAct especially effective for research, troubleshooting, and exploratory workflows." — Use case analysis

"The cycle involves thoughts (decomposing tasks), actions (using tools/APIs), and observations (processing results) that inform subsequent reasoning." — Pattern mechanics

## Related Terms
- Chain-of-Thought (CoT)
- Tool Use / Function Calling
- Agent Framework
- MCP (Model Context Protocol)
- Autonomous Development Loop

## Relevance to Generative AI Engineer Role
ReAct is the pattern you'll use for sophisticated agents that combine reasoning with action. You'll design agent loops, define available tools, and implement observation processing. Understanding ReAct helps you debug agent failures (where did it go wrong—reasoning or action?) and design agents that improve iteratively.

Sources:
- [Prompt Engineering Guide: ReAct](https://www.promptingguide.ai/techniques/react)
- [IBM: ReAct Agent Explanation](https://www.ibm.com/think/topics/react-agent)
- [Microsoft Azure: Agent Design Patterns](https://azure.microsoft.com/en-us/blog/agent-factory-the-new-era-of-agentic-ai-common-use-cases-and-design-patterns/)
