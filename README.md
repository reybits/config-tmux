# Easy TMUX

A streamlined and customizable TMUX configuration for enhanced terminal productivity.

![TMUX session](https://github.com/andreyugolnik/config-tmux/blob/master/tmux-session.png?raw=true)

## Features

- **Seamless Vim / Neovim Integration** – Smooth workflow between TMUX and your favorite editor.
- **Session Management with fzf** – Quickly switch between sessions using fuzzy finding.
- **Lightweight Yet Functional Theme** – A clean and minimal look without sacrificing usability.
- **Mouse & Keybindings Enhancements** – Improved navigation and pane management.
- **Clipboard Support** – Easily copy and paste between TMUX and your system clipboard.
- **Optimized for Performance** – Minimal overhead while maintaining essential features.

## Install

1. Clone repository.
```sh
$ git clone https://github.com/andreyugolnik/config-tmux.git
```

2. Initialize submodule.
```sh
$ git submodule update --init
```

3. Link to the XDG-config path.
```sh
$ ln -s /path/to/config-tmux/tmux ~/.config/tmux
```

4. Withing tmux install all plugins.
`prefix + I`


## Useful keys
- `prefix + f` - open / attach session
- `prefix + R` - reload config
- `prefix + I` - install pulugins
- `prefix + U` - update plugins
- `prefix + alt + u` - uninstall plugins
