# Configuration

## Reason to have configuration

This program can be used without a configuration file. But you may want to have a configuration file to:

- Set up a keyboard layout for a specific window classes

## Configuration file

Create a file
~/.config/hyprland-per-window-layout/options.toml

Example configuration file:

```toml
# list of keyboards to operate on
# use `hyprctl devices -j` to list all keyboards
keyboards = [
  "lenovo-keyboard",
]

# layout_index => window classes list
# use `hyprctl clients` to get class names
[[default_layouts]]
1 = [
    "org.telegram.desktop",
]
```

This example will set your second layout for the Telegram by default.

1 - is a layout index. In case of this input configuration:
```
input {
  kb_layout = us,es,de
  ...
```
*us* index is 0, *es* index is 1, *de* index is 2.

Note, *keyboards* section is required for default_layouts feature.

Here is more complex example if you have 3 layouts and 2 keyboards:

```toml
# list of keyboards to operate on
# use `hyprctl devices -j` to list all keyboards
keyboards = [
  "apple-magic-keyboard",
  "lenovo-keyboard",
]

# layout_index => window classes list
# use `hyprctl clients` to get class names
[[default_layouts]]
1 = [
    "org.telegram.desktop",
    "discord",
]
2 = [
    "firefox",
]
```

## Layout file

The program can write the current layout name to a file every time the layout changes. This is useful for displaying the active layout in a status bar (e.g. Waybar) by simply reading a file.

The file always contains a single line with the short XKB layout name, for example:
```
us
```

This feature works automatically with no configuration needed. By default the file is written to:
```
~/.cache/kb_layout
```

To use a different path, set `kb_layout_file` in your `options.toml`:

```toml
kb_layout_file = "~/.cache/kb_layout"
```

The path supports `~/` expansion. The file is created automatically if it does not exist.

### Example: Waybar integration

Add a custom module to your Waybar config (`~/.config/waybar/config`):

```json
"custom/layout": {
    "exec": "cat $HOME/.cache/kb_layout",
    "interval": 1,
    "format": " {}"
}
```

Or use `inotify-tools` for instant updates without polling:

```json
"custom/layout": {
	"exec": "cat $HOME/.cache/kb_layout",
    "signal": 1,
    "format": " {}"
}
```
You should run script for this:

`KbLayoutWathcer.sh`
```bash  
#!/usr/bin/env bash

FILE="$HOME/.cache/kb_layout"

while inotifywait -e close_write "$FILE"; do
    pkill -RTMIN+1 waybar
done
```
And use `exec-once = KbLayoutWathcer.sh` at system startup
