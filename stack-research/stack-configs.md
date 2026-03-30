# Stack-Specific Keybinding Configs
## Ghostty + tmux + Zsh/zsh-vi-mode + Neovim/LazyVim + Claude Code CLI

---

## 1. Community Dotfiles Using This Stack

- [joshukraine/dotfiles](https://github.com/joshukraine/dotfiles) — macOS dotfiles: Neovim (LazyVim), Zsh, Ghostty, tmux, GNU Stow, Starship, claude-code.nvim
- [Gentleman-Programming/Gentleman.Dots](https://github.com/Gentleman-Programming/Gentleman.Dots) — LazyVim + Ghostty + tmux + Zsh, installable via Homebrew
- [phansch/dotfiles](https://github.com/phansch/dotfiles) — Ghostty + tmux + Neovim (LazyVim) + Zsh, CI-tested weekly
- [nicknisi/dotfiles](https://github.com/nicknisi/dotfiles) — Popular long-running dotfiles: vim + zsh + tmux + lazy.nvim
- [codexstar69 gist](https://gist.github.com/codexstar69/584435935a35e95e406d4be1dda07afa) — Complete macOS setup with Catppuccin Mocha theme

### Emerging Patterns
- **Catppuccin Mocha** — dominant theme across Ghostty + Neovim + tmux
- **Starship prompt** — most popular prompt replacement
- **GNU Stow** — standard dotfile management tool

---

## 2. tmux Prefix Key Recommendation

| Prefix | Pros | Cons |
|--------|------|------|
| `Ctrl-b` (default) | No conflicts out of box | Awkward stretch; conflicts with Vim `Ctrl-b` (page up) |
| `Ctrl-a` (popular) | Ergonomic, GNU Screen familiar | Conflicts with shell "go to beginning of line" |
| `Ctrl-Space` (**recommended**) | Easy to hit; mirrors Vim `<Space>` leader; no shell conflicts | Some IME conflicts |

### Why Ctrl-Space
1. Mirrors common Neovim leader key (`<Space>`) — conceptual consistency
2. No conflict with Vim's `Ctrl-b` or `Ctrl-a`
3. No conflict with shell readline
4. Space bar is the largest key — hard to miss

```tmux
unbind-key C-b
set-option -g prefix C-Space
bind-key C-Space send-prefix
```

Sources: [dev.to](https://dev.to/reprintsev/my-favorite-tmux-prefix-2618) · [koenwoortman.com](https://koenwoortman.com/tmux-prefix-ctrl-space/) · [hamvocke.com](https://hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/) · [tmuxai.dev](https://tmuxai.dev/tmux-prefix/)

---

## 3. Pane Navigation: smart-splits.nvim vs vim-tmux-navigator

| Plugin | Navigation | Resizing | Performance |
|--------|-----------|----------|-------------|
| vim-tmux-navigator | Ctrl-h/j/k/l | No | Shells out to `ps` every keypress — can lag |
| nvim-tmux-navigation | Ctrl-h/j/k/l | No | Similar shell-out |
| **smart-splits.nvim** | Ctrl-h/j/k/l | Alt-h/j/k/l | Uses `@pane-is-vim` tmux var — no shell-out ✅ |

### Recommendation: smart-splits.nvim

```lua
{
  "mrjones2014/smart-splits.nvim",
  lazy = false,
  keys = {
    { "<C-h>", function() require("smart-splits").move_cursor_left() end },
    { "<C-j>", function() require("smart-splits").move_cursor_down() end },
    { "<C-k>", function() require("smart-splits").move_cursor_up() end },
    { "<C-l>", function() require("smart-splits").move_cursor_right() end },
    { "<A-h>", function() require("smart-splits").resize_left() end },
    { "<A-j>", function() require("smart-splits").resize_down() end },
    { "<A-k>", function() require("smart-splits").resize_up() end },
    { "<A-l>", function() require("smart-splits").resize_right() end },
  },
}
```

Sources: [smart-splits.nvim](https://github.com/mrjones2014/smart-splits.nvim) · [medium.com/@karpov-kir](https://medium.com/@karpov-kir/nvim-tmux-smart-navigation-and-resizing-on-macos-6bcb3c1d0e02) · [brianschiller.com](https://brianschiller.com/blog/2024/07/17/neovim-smart-splits-on-macos/)

---

## 4. Copy Mode — macOS Clipboard (No wrapper needed on macOS 11+ / tmux 3.2+)

```tmux
setw -g mode-keys vi
bind -T copy-mode-vi v send-keys -X begin-selection
bind -T copy-mode-vi V send-keys -X select-line
bind -T copy-mode-vi C-v send-keys -X rectangle-toggle
bind -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"
bind -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel "pbcopy"
bind -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel "pbcopy"
```

Sources: [thoughtbot.com](https://thoughtbot.com/blog/tmux-copy-paste-on-os-x-a-better-future) · [jdeen.com](https://www.jdeen.com/blog/tmux-on-macos-copy-to-system-clipboard) · [tmux-yank](https://github.com/tmux-plugins/tmux-yank)

---

## 5. zsh-vi-mode + tmux: Escape-Time & KEYTIMEOUT

| Setting | File | Recommended Value |
|---------|------|-------------------|
| `escape-time` | `~/.tmux.conf` | `0` |
| `KEYTIMEOUT` | `~/.zshrc` | `1` (= 10ms) |
| `ttimeoutlen` | Neovim | `5` to `10` ms |

```zsh
export KEYTIMEOUT=1
ZVM_READKEY_ENGINE=$ZVM_READKEY_ENGINE_NEX
# Fix fzf Ctrl-R conflict
zvm_after_init_commands+=('[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh')
```

Sources: [johnhawthorn.com](https://www.johnhawthorn.com/2012/09/vi-escape-delays/) · [devedge.github.io](https://devedge.github.io/2025/05/09/eliminating-esc-delays-in-tmux-vim-and-zsh/) · [jeffreytse/zsh-vi-mode](https://github.com/jeffreytse/zsh-vi-mode)

---

## 6. Claude Code CLI Integration

### Claude Code Popup (Persistent Session)
```tmux
bind C-c display-popup -d "#{pane_current_path}" -xC -yC -w 80% -h 80% -E \
  "tmux new-session -A -s claude 'claude'"
```
`Prefix + Ctrl-c` → popup → dismiss → session persists

### Neovim Auto-Reload (for Claude external edits)
```lua
vim.opt.autoread = true
vim.api.nvim_create_autocmd({"FocusGained", "BufEnter"}, { command = "checktime" })
```

### Neovim Plugins
- [claudecode.nvim](https://github.com/coder/claudecode.nvim) — WebSocket MCP protocol (same as VS Code extension)
- [claude-code.nvim](https://github.com/dreemanuel/claude-code.nvim) — tmux integration: `<leader>af`, `<leader>as`, `<leader>at`
- [avante.nvim](https://github.com/yetone/avante.nvim) — Cursor-like multi-model AI in Neovim

### Extended Keys for Ghostty
```tmux
set -s extended-keys on
set -s extended-keys-format csi-u
set -as terminal-features 'xterm-ghostty:extkeys'
```

Sources: [code.claude.com/docs](https://code.claude.com/docs/en/terminal-config) · [devas.life](https://www.devas.life/how-to-run-claude-code-in-a-tmux-popup-window-with-persistent-sessions/) · [hboon.com](https://hboon.com/using-tmux-with-claude-code/)

---

## 7. Critical tmux.conf

```tmux
unbind C-b
set -g prefix C-Space
bind C-Space send-prefix
set -sg escape-time 0
set -s extended-keys on
set -s extended-keys-format csi-u
set -as terminal-features 'xterm-ghostty:extkeys'
set -g allow-passthrough on
set -g focus-events on
set -g mouse on
setw -g mode-keys vi
bind -T copy-mode-vi v send-keys -X begin-selection
bind -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"
bind C-c display-popup -d "#{pane_current_path}" -xC -yC -w 80% -h 80% -E \
  "tmux new-session -A -s claude 'claude'"
set -g history-limit 50000
set -g base-index 1
setw -g pane-base-index 1
set -g default-terminal "tmux-256color"
set -ag terminal-overrides ",xterm-ghostty:RGB"
```
