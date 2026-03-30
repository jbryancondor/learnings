# Best Stack for Generative AI Roles
## Research Report: AI-Native Terminal Workflows in 2026

---

## 1. What Prominent AI Engineers Actually Use

### Anthropic
- **Boris Cherny** (head of Claude Code): 100% of his code is now AI-written using Claude Code + Opus. Company-wide: AI writes 70-90% of code. Claude Code writes ~90% of its own codebase.
- **Dario Amodei**: Some engineers have stopped writing code themselves — focusing on editing and directing AI instead.

Source: [Fortune, Jan 2026](https://fortune.com/2026/01/29/100-percent-of-code-at-anthropic-and-openai-is-now-ai-written-boris-cherny-roon/)

### Andrej Karpathy (ex-OpenAI, ex-Tesla AI)
- Coined "vibe coding" (Feb 2025) — 4.5M views, Collins Word of the Year.
- Setup: **Cursor Composer + Claude Sonnet + SuperWhisper** (voice input). Barely touches keyboard.
- By Feb 2026, evolved to "agentic engineering" — orchestrating autonomous AI agents with structured oversight: *"You are not writing the code directly 99% of the time."*
- Released **AutoResearch** (630 lines Python) for autonomous ML research on single GPU.

Sources: [Latent Space](https://www.latent.space/p/s3) · [abhs.in — AutoResearch](https://www.abhs.in/blog/andrej-karpathy-autoresearch-autonomous-ai-ml-experiments-2026)

### Simon Willison (co-creator Django)
- "Writing code is cheap now" — focus shifts from writing to orchestrating AI.
- If you review, test, and understand AI-generated code, that's professional practice, not "vibe coding."

Source: [simonwillison.net](https://simonwillison.net/tags/andrej-karpathy/)

### General AI Industry Pattern
- ~50% of devs at AI/ML startups use **Vim or Helix**, rest use VS Code or PyCharm.
- Most productive setup: **an IDE agent for daily work + a terminal agent for hard problems**.
- Most experienced AI developers use 2-3 tools together.

---

## 2. Your Stack's AI-Native Score

| Capability | Score | Notes |
|---|---|---|
| Fast model invocation | ★★★★★ | Claude Code is terminal-native |
| Context switching | ★★★★★ | tmux panes are the fastest way to switch |
| Session persistence | ★★★★★ | tmux's killer feature for long AI tasks |
| Multi-agent orchestration | ★★★★☆ | Agent Teams work in tmux; layout issues exist |
| File hot-reload | ★★★☆☆ | Requires config; LazyVim's checktime helps |
| Notebook integration | ★★☆☆☆ | Neopyter bridge exists but is immature |
| Eval/log monitoring | ★★★★★ | Dedicated tmux panes ideal |
| Model flexibility | ★★★☆☆ | Claude Code is Anthropic-only; avante.nvim adds multi-model |
| Resource overhead | ★★★★★ | Ghostty < 100MB, minimal CPU vs Electron IDEs |

**Verdict: Near-optimal for AI-native terminal-first work in 2026.**

Source: [xata.io — Configuring Neovim for Coding Agents](https://xata.io/blog/configuring-neovim-coding-agents) · [Duy NG — Rise of Terminal Tools](https://tduyng.com/blog/rise-of-terminal/)

---

## 3. Recommended Enhancements (Priority Order)

1. **[claudecode.nvim](https://github.com/coder/claudecode.nvim)** — WebSocket MCP integration (same protocol as VS Code extension)
2. **[avante.nvim](https://github.com/yetone/avante.nvim)** — Cursor-like experience, multi-model (Claude, GPT, Gemini, Ollama)
3. **Auto-reload buffers** — File-watcher based hot-reload for live Claude Code changes
4. **[diffview.nvim](https://github.com/sindrets/diffview.nvim) with auto-refresh** — Live diff view for AI changes
5. **Path-yanking keybindings** — `<leader>yr` (relative) / `<leader>ya` (absolute) for quick code references
6. **[Neopyter](https://github.com/SUSTech-data/neopyter)** — Edit in Neovim, run in JupyterLab (for ML experimentation)
7. **[Aider](https://aider.chat)** — Complement for routine git-first changes (4.2x fewer tokens than Claude Code)
8. **[claude-tmux](https://github.com/nielsgroen/claude-tmux)** — TUI for managing multiple Claude Code sessions with git worktree

---

## 4. tmux Session Layouts for AI Work

### Pattern 1: Solo AI Development (Most Common)
```
Window 1: "code"  — Neovim (left 60%) | Claude Code (right 40%)
Window 2: "run"   — Server/model running | Logs (tail -f)
Window 3: "eval"  — Eval pipeline | Results viewer
Window 4: "git"   — Git operations | PR reviews
```

### Pattern 2: Multi-Agent Orchestration
```
Window 1: "agents"  — Lead Agent | Worker 1 | Worker 2 | Worker 3
Window 2: "code"    — Neovim (full screen, with claudecode.nvim)
Window 3: "monitor" — htop | GPU stats (nvidia-smi) | Logs
```

### Pattern 3: LLM Application Development
```
Window 1: "dev"  — Neovim | Claude Code side-by-side
Window 2: "api"  — LLM API server (Ollama/vLLM) | curl/httpie testing
Window 3: "eval" — Running evals | Comparing outputs
Window 4: "data" — JupyterLab (via neopyter) | Data exploration
```

### Multi-Agent Session Managers
- **[Agent of Empires (aoe)](https://github.com/njbrake/agent-of-empires)** — Rust-based tmux manager for parallel AI agents
- **[NTM](https://github.com/Dicklesworthstone/ntm)** — TUI for orchestrating multiple AI agents in tiled panes
- **[claude-tmux](https://github.com/nielsgroen/claude-tmux)** — TUI managing Claude Code sessions with worktree + PR support

### Known Issues
- Agent Teams splitting current tmux window can break existing layouts ([GitHub #23615](https://github.com/anthropics/claude-code/issues/23615))
- Split-pane mode NOT supported in Ghostty as of March 2026

---

## 5. Alternatives Through AI-Native Lens

### Cursor IDE
- Used by 50%+ Fortune 500, Karpathy's choice for vibe coding.
- **Strengths**: Best tab completions, visual inline diffs, codebase indexing, Background Agents.
- **Weaknesses**: Proprietary, Electron-based (500-800MB RAM), $20/mo, no Neovim integration.
- **For Gen AI work**: Best for those who want AI to do everything in one place. Not great for multi-agent orchestration or running eval pipelines.

Source: [cursor.com](https://cursor.com/)

### Zed Editor
- Rust-based, GPU-accelerated, open source. 200ms cold start.
- **Strengths**: ACP (Agent Client Protocol) integrates Claude Code, Gemini CLI, Codex CLI natively. Real-time collaboration.
- **AI verdict**: Best companion for CLI-based AI agents — Zed's lightweight engine means zero performance degradation when running Claude Code alongside it.

Sources: [Zed vs Cursor 2025](https://www.f22labs.com/blogs/zed-vs-cursor-ai-the-ultimate-2025-comparison-guide/) · [builder.io](https://www.builder.io/blog/zed-ai-2026)

### Windsurf IDE
- VS Code fork with Cascade (agentic multi-file reasoning). $15/mo.
- **AI verdict**: Good for onboarding, not for power users doing Gen AI work.

Source: [windsurf.com](https://windsurf.com/)

### VSCode + Continue.dev
- Open-source AI assistant. BYO model (Claude, GPT, Gemini, local). Free.
- **AI verdict**: Best open-source in-editor option for teams needing privacy/model flexibility.

Source: [continue.dev](https://www.continue.dev/)

### Aider (Terminal-based)
- Model-agnostic, git-first. 52.7% SWE-bench. 4.2x fewer tokens than Claude Code.
- **AI verdict**: Best complement to Claude Code for routine changes. Use Aider for repetitive tasks, Claude Code for complex multi-step.

Source: [Aider vs Claude Code](https://zenvanriel.com/ai-engineer-blog/aider-vs-claude-code/)

### OpenCode (Terminal-based)
- Open-source Claude Code alternative. 120K+ stars, 75+ AI providers. Air-gapped mode.
- **AI verdict**: Best for model flexibility in a terminal agent.

Source: [opencode.ai](https://opencode.ai/)

### JupyterLab
- Essential for ML experimentation phases. Jupyter AI extension provides `%%ai` magic with Anthropic/OpenAI support.
- Use alongside Neovim via Neopyter, not instead of it.

Source: [jupyter-ai](https://github.com/jupyterlab/jupyter-ai)

---

## 6. When to Consider Switching

| If you need... | Consider... |
|---|---|
| Fastest path idea → prototype | Cursor IDE (Karpathy's choice) |
| Real-time collaboration | Zed Editor |
| Model flexibility in terminal | OpenCode or Aider |
| Notebook-heavy ML research | JupyterLab + Jupyter AI |
| Multiple AI agents in parallel | Agent of Empires or NTM |

**The only scenario where switching makes clear sense**: 50%+ of time on visual UI work or collaborative editing — then Zed or Cursor as primary editor, with Claude Code still in tmux.

---

## 7. The Bigger Picture: Agentic Engineering (2026)

The terminal-first approach is increasingly validated as the professional pattern — moving beyond "vibe coding" to **"agentic engineering"** where you orchestrate AI agents rather than write code directly.

> *"You are not writing the code directly 99% of the time."* — Andrej Karpathy, 2026

Your stack (Ghostty + tmux + Neovim + Claude Code) is purpose-built for this:
- tmux = agent session manager
- Neovim = code reviewer and context provider
- Claude Code = the agent doing the work
- Ghostty = the fastest window to all of it

Source: [Ghostty best all-rounder Mac 2026](https://scopir.com/posts/best-terminal-emulators-developers-2026/)
