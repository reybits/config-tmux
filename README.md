# Easy TMUX

A streamlined and customizable TMUX configuration for enhanced terminal productivity.

![TMUX session](https://github.com/reybits/config-tmux/blob/master/tmux-session.png?raw=true)

## Features

- **Seamless Vim / Neovim Integration** – Smooth workflow between TMUX and your favorite editor.
- **Session Management with fzf** – Quickly switch between sessions using fuzzy finding, ordered by most recent use, with a live preview of each session.
- **Claude Code Waiting Indicator** – See at a glance which sessions have a Claude Code instance waiting for your input, both in the status bar and the session picker.
- **Lightweight Yet Functional Theme** – A clean and minimal look without sacrificing usability.
- **Mouse & Keybindings Enhancements** – Improved navigation and pane management.
- **Clipboard Support** – Easily copy and paste between TMUX and your system clipboard.
- **Optimized for Performance** – Minimal overhead while maintaining essential features.

## Install

1. Clone repository.
```sh
git clone https://github.com/reybits/config-tmux.git
```

2. Initialize submodule.
```sh
git submodule update --init
```

3. Link to the XDG-config path.
```sh
ln -s /path/to/config-tmux/tmux ~/.config/tmux
```

4. Withing tmux install all plugins.
`prefix + I`

## Useful keys
- `prefix + f` - open / attach session
- `prefix + R` - reload config
- `prefix + I` - install pulugins
- `prefix + U` - update plugins
- `prefix + alt + u` - uninstall plugins

## Claude Code waiting indicator

When a Claude Code instance in any session is waiting for you — it finished a
turn, is asking for permission, or is idle at the prompt — the status bar shows
it on the right as `✻ <session>`, and the session picker (`prefix + f`) marks
those sessions with a red `✻`. The mark clears as soon as you switch to that
window or answer Claude.

The tmux side is already wired up: helper scripts in `tmux/bin/`
(`tmux-claude-mark`, `tmux-claude-waiting`, `tmux-claude-status`) plus the
`status-right` and navigation hooks in `tmux.conf`. To feed them, Claude Code
must report its state through hooks. Merge the following into
`~/.claude/settings.json`:

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          { "type": "command", "command": "$HOME/.config/tmux/bin/tmux-claude-mark wait" }
        ]
      }
    ],
    "Notification": [
      {
        "matcher": "permission_prompt|idle_prompt",
        "hooks": [
          { "type": "command", "command": "$HOME/.config/tmux/bin/tmux-claude-mark wait" }
        ]
      }
    ],
    "UserPromptSubmit": [
      {
        "hooks": [
          { "type": "command", "command": "$HOME/.config/tmux/bin/tmux-claude-mark clear" }
        ]
      }
    ]
  }
}
```

Claude Code picks up hook changes live, so no restart is needed. The feature is
optional — without the hooks nothing is marked and the indicator never appears.
See the [hooks reference](https://code.claude.com/docs/en/hooks) for details.
