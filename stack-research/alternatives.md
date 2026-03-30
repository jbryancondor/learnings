# Alternative Terminal Stacks + Universal Vim Keybindings

---

## PART A — Alternative Stacks Comparison

| Feature | Ghostty+tmux (Current) | WezTerm | Zellij | Kitty+tmux | Alacritty+tmux | Warp | Rio |
|---|---|---|---|---|---|---|---|
| Built-in Multiplexing | No (needs tmux) | Yes | IS the multiplexer | No | No | Yes | No |
| Performance | **Fastest** (2-5x faster) | Good, heavier | Good (Rust) | Excellent | Excellent | Good | Fast (WebGPU) |
| macOS Native Feel | **Best** — Metal renderer | Cross-platform | Good | Own window mgmt | Minimal UI | Polished but SaaS | Cross-platform |
| Config Style | INI key=value | Lua scripting | YAML/KDL | Single file | TOML | GUI + config | TOML |
| Keybinding Philosophy | tmux prefix-key model | Custom Lua | **Modal (like Vim!)** | tmux prefix-key | tmux prefix-key | Modern shortcuts | Standard |
| Beginner-Friendly | Medium | Medium | **Best** — keybinding bar | Medium | Medium-Low | High | Low |
| AI Integration | Claude Code (external) | None | None | None | None | **Built-in agents** | None |
| Stars/Maturity | 45K+, launched Dec 2024 | Mature, large community | Growing, active | Since 2017 | Mature, stable | VC-funded, SaaS | Early-stage |

### WezTerm
**Best if:** you want to eliminate tmux entirely and need cross-platform (including Windows).
**Trade-off:** 2-5x slower than Ghostty, Lua learning curve.
Sources: [Ghostty vs WezTerm 2026](https://scopir.com/posts/ghostty-vs-wezterm-2026/) · [Modern Terminal Emulators 2026](https://calmops.com/tools/modern-terminal-emulators-2026-ghostty-wezterm-alacritty/) · [macOS Terminal Comparison 2025](https://medium.com/@dynamicy/choosing-a-terminal-on-macos-2025-iterm2-vs-ghostty-vs-wezterm-vs-kitty-vs-alacritty-d6a5e42fd8b3)

### Zellij
**Best if:** you're a beginner or modal-thinking developer. Context-aware keybinding bar shows available actions — lowest learning curve.
**Watch out for:** Neovim mode conflicts — install [zellij-autolock](https://github.com/fresh2dev/zellij-autolock) plugin.
Sources: [Zellij vs tmux](https://dasroot.net/posts/2026/02/terminal-multiplexers-tmux-vs-zellij-comparison/) · [tmux vs Zellij Guide](https://tmuxai.dev/tmux-vs-zellij/) · [Zellij Impressions](https://keyholesoftware.com/zellij-the-impressions-of-a-casual-tmux-user/)

### Kitty
**Best if:** you need deep scriptability or the richest TUI/image ecosystem.
**Watch out for:** Less native macOS feel, no Windows support.
Sources: [Kitty vs Ghostty](https://itsfoss.com/comparison/ghostty-vs-kitty/) · [Ghostty to Kitty](https://linkarzu.com/posts/terminals/ghostty-to-kitty/) · [Modern Terminals Showdown](https://blog.codeminer42.com/modern-terminals-alacritty-kitty-and-ghostty/)

### Alacritty + tmux
**Best if:** you need Windows support or have existing dotfiles.
**Watch out for:** Won't add tabs/splits by design. True-color with tmux+Neovim requires config work.
Sources: [Alacritty Workflow](https://haseebmajid.dev/posts/2023-05-02-my-development-workflow-with-alacritty-fish-tmux-nvim/) · [True Color Config](https://www.lorenzobettini.it/2025/10/configure-tmux-to-support-true-color-and-italics-in-alacritty-and-neovim/)

### Warp
**Different category — ADE, not a traditional terminal.**
Mandatory login, $15/month, no tmux compatibility, closed source. Not suitable for Vim-centric keyboard-driven workflow.
Sources: [Warp Agentic](https://thenewstack.io/how-warp-went-from-terminal-to-agentic-development-environment/) · [Terminal Evolution 2026](https://rentierdigital.xyz/blog/the-terminal-just-evolved-for-the-first-time-in-50-years-not)

### Stack Decision Matrix

| If you want... | Choose... |
|---|---|
| Best macOS native + performance | **Ghostty + tmux** (current) ✅ |
| Eliminate tmux entirely | **WezTerm** |
| Easier multiplexer for beginners | **Ghostty + Zellij** |
| Maximum scriptability | **Kitty** |
| Proven + Windows support | **Alacritty + tmux** |
| AI-first, less keyboard-driven | **Warp** (SaaS trade-offs) |

---

## PART B — Universal Vim Keybindings (Never Change)

### The Grammar Rule
Vim uses **Verb + Noun** grammar. Works identically in: Vim, Neovim, LazyVim, VSCodeVim, IdeaVim, Zed, XCode.

Sources: [Vim Grammar](https://learnvim.irian.to/basics/vim_grammar/) · [The Vim Language](https://www.ssp.sh/brain/vim-language-and-motions/) · [freeCodeCamp Vim Explained](https://www.freecodecamp.org/news/vim-language-and-motions-explained/)

### Core Motions (100% Universal)
| Motion | Action |
|---|---|
| `h` `j` `k` `l` | Left / Down / Up / Right |
| `w` / `b` / `e` / `ge` | Word forward / back / end / back-end |
| `0` / `$` / `^` | Start / End / First non-blank of line |
| `gg` / `G` | First / Last line |
| `Ctrl-d` / `Ctrl-u` | Half-page down / up |
| `%` | Jump to matching bracket |
| `H` `M` `L` | Top / Middle / Bottom of screen |

### Find Motions (100% Universal)
| Motion | Action |
|---|---|
| `f{char}` / `F{char}` | Find next/prev char on line |
| `t{char}` / `T{char}` | Till next/prev char (before it) |
| `;` / `,` | Repeat last f/F/t/T forward/backward |

### Operators/Verbs (100% Universal)
| Operator | Action | Examples |
|---|---|---|
| `d` | Delete | `dw`, `d$`, `dd` |
| `c` | Change (delete + insert) | `cw`, `c$`, `cc` |
| `y` | Yank (copy) | `yw`, `y$`, `yy` |
| `>` / `<` | Indent right / left | `>>`, `>ap` |
| `gu` / `gU` | Lowercase / Uppercase | `guiw`, `gUU` |

### Text Objects (100% Universal)
Work with `i` (inner) and `a` (around):
`ciw` `ci"` `ci(` `ci{` `ci[` `ci<` `cit` — change inside word/quotes/brackets/tag
`diw` `di"` `di(` — delete inside
`yiw` `yi"` `yi(` — yank inside
`daw` `da"` `da(` — delete around (includes delimiters)

### Insert Mode (100% Universal)
`i` / `a` / `I` / `A` / `o` / `O` / `s` / `S` + `Esc` to return

### Search (100% Universal)
`/pattern` forward, `?pattern` backward, `n`/`N` next/prev, `*`/`#` word under cursor

### Marks (100% Universal)
`m{a-z}` set mark, `` `{a-z} `` jump exact, `'{a-z}` jump to line

### Registers (100% Universal)
`"{a-z}y{motion}` yank into register, `"{a-z}p` paste, `"0` last yank, `"+` system clipboard

### Macros (100% Universal)
`q{a-z}` start recording, `q` stop, `@{a-z}` play, `@@` replay last

### Visual Mode (100% Universal)
`v` char, `V` line, `Ctrl-v` block, `gv` reselect, `o` toggle selection end

### Dot Repeat (100% Universal)
`.` — repeat last change. One of the highest-leverage motions in Vim.

### Compatibility Matrix
| Feature | Vim | LazyVim | VSCodeVim | IdeaVim | Zed | XCode |
|---|---|---|---|---|---|---|
| hjkl + motions | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| f/t/F/T | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Text objects (ci/di/yi) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Operators (d/c/y/>/< ) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Visual mode | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Search (//?/n/N) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Marks | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Registers | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Macros | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Dot repeat | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

Sources: [Vim Keybindings Everywhere](https://github.com/erikw/vim-keybindings-everywhere-the-ultimate-list) · [VSCodeVim](https://github.com/VSCodeVim/Vim) · [IdeaVim](https://github.com/JetBrains/ideavim)

### NOT Universal (editor-specific)
- `:commands` (Ex commands) — varies by editor
- `Ctrl-w` splits — each editor handles differently
- Buffer/tab navigation — editor-specific
- Plugin mappings (`gcc`, `cs"'`) — need plugin support

### The 30-Command Beginner Safe List
```
MOVEMENT:   hjkl  w/b  e  0/$  gg/G  Ctrl-d/u  f{c}/t{c}  ;/,  %
EDITING:    i/a/I/A/o/O  Esc  dd/yy/p  u/Ctrl-r  .
TEXT OBJS:  ciw  ci"  ci(  diw/di"/di(  yiw  daw/da"
SEARCH:     /pattern  n/N  *
POWER:      q{a-z}...q  @{a-z}  v/V/Ctrl-v
```

### Learning Resources
1. **vimtutor** — Built-in, free, 30 min/day
2. **[Vim Adventures](https://vim-adventures.com/)** — Gamified ($25, first level free)
3. **[VimHero](https://www.vim-hero.com/)** — Interactive browser tutorial
4. **[ThePrimeagen's Vim Fundamentals](https://theprimeagen.github.io/vim-fundamentals/)** — Best structured course
5. **[MIT Missing Semester](https://missing.csail.mit.edu/2020/editors/)** — Free, concise
6. **[vim-be-good](https://github.com/ThePrimeagen/vim-be-good)** — Neovim plugin, game-based practice
7. **[Learn-Vim (GitHub)](https://github.com/iggredible/Learn-Vim)** — Comprehensive free guide

Sources: [Class Central Vim Courses](https://www.classcentral.com/report/best-vim-courses/) · [Slant Vim Resources](https://www.slant.co/topics/411/~best-resources-for-learning-vim)
