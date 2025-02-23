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
