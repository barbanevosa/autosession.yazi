# autosession.yazi
A [Yazi](https://github.com/sxyazi/yazi) plugin for automatic session persistence that saves the current state on exit and restores the last saved state on startup.

> [!IMPORTANT]
> This plugin conflicts with [project.yazi](https://github.com/MasouShizuka/projects.yazi) when the latter is configured with `load_after_start = true` or `update_before_quit = true`.
> Use only one plugin for automatic session persistence (disable/remove the other).

## Features
The plugin saves Yazi workspace state on exit and restores it on startup:
 - open tabs with their working directories,
 - per-tab view settings (sorting mode, linemode, hidden file visibility),
 - active tab selection.

## Installation
```
ya pkg add barbanevosa/autosession
```

## Setup
Add the following configuration entries to their respective configuration files:

### init.lua
```lua
-- ~/.config/yazi/init.lua
require("autosession"):setup()
```

### keymap.toml
```toml
# ~/.config/yazi/keymap.toml
[mgr]
prepend_keymap = [
    { on = [ "q" ], run = "plugin autosession -- save-and-quit", desc = "Save session and quit" },
]
```
## Acknowledgments
Special thanks to **Masou Shizuka** ([@MasouShizuka](https://github.com/MasouShizuka)) for creating [projects.yazi](https://github.com/MasouShizuka/projects.yazi), which served as the initial inspiration and learning resource for this plugin.
