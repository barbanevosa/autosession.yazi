# autosession.yazi
A [Yazi](https://github.com/sxyazi/yazi) plugin for automatic session persistence that saves the current state on exit and restores the last saved state on startup.

> [!IMPORTANT]
> This plugin conflicts with [project.yazi](https://github.com/MasouShizuka/projects.yazi) if you use the latter with options `load_after_start = true` or `update_before_quit = true`.
> Use only one plugin for automatic session persistence (disable/remove the other).

## Features
This plugin allows saving Yazi workspace state and restoring it on startup:
 - Automatically restores the last stored state on startup
 - Store the current state
 - Erase the last stored state 

Where the workspace state includes:
 - Open tabs with their working directories
 - Per-tab view settings: sorting mode, linemode, hidden file visibility
 - Active tab selection

## Installation
```bash
ya pkg add barbanevosa/autosession
```

## Setup
Add the following configuration entries to their respective configuration files:

### Plugin options in `init.lua`
```lua
-- ~/.config/yazi/init.lua
require("autosession"):setup()
```

### Keybindings in `keymap.toml`
To store the state and quit:
```toml
# ~/.config/yazi/keymap.toml
[[mgr.prepend_keymap]]
on = "q"
run = "plugin autosession -- save-and-quit"
desc = "Store the current session and quit the application"
```

To erase the currently stored state and quit without outputting the cwd:
```toml
# ~/.config/yazi/keymap.toml
[[mgr.prepend_keymap]]
on = "Q"
run = "plugin autosession -- erase-and-quit-no-cwd"
desc = "Erase the current session and quit without outputting cwd-file"
```

To simply store the state:
```toml
# ~/.config/yazi/keymap.toml
[[mgr.prepend_keymap]]
on = "<C-s>"
run = "plugin autosession -- save"
desc = "Store the current session"
```

To simply erase the currently stored state:
```toml
# ~/.config/yazi/keymap.toml
[[mgr.prepend_keymap]]
on = "<C-e>"
run = "plugin autosession -- erase"
desc = "Erase the current session"
```

## Usage
By default, press `q` to save session and quit.

> [!NOTE]
> Session saving requires Yazi to complete its **normal quit** workflow. Abnormal termination (crashes, force-quit) results in current session loss.
>
> The default `q` keybinding for save-and-quit can be remapped in `keymap.toml`.

## Acknowledgments
Special thanks to **Masou Shizuka** ([@MasouShizuka](https://github.com/MasouShizuka)) for creating **[projects.yazi](https://github.com/MasouShizuka/projects.yazi)**, which served as the initial inspiration and learning resource for this plugin.

## License
**autosession.yazi** is MIT-licensed. For more information check the [LICENSE](LICENSE) file.
