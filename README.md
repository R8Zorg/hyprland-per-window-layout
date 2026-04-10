# Hyprland Per-Window Keyboard Layout Manager

Automatic keyboard layout switching for Hyprland - each window remembers its own keyboard layout.

## Features

- 🚀 **Zero configuration** - works out of the box
- 🧠 **Per-window memory** - each window maintains its layout
- ⚡ **Lightweight** - minimal resource usage (Rust)
- 🔧 **Optional configuration** - set default layouts per application

## Use Cases

- **Developers**: Code in English, chat in native language
- **Multilingual users**: Seamless switching between languages
- **Power users**: Consistent layouts across applications

**Requirements**: At least 2 keyboard layouts in hyprland.conf

## Installation

### From [AUR](https://aur.archlinux.org/packages/hyprland-per-window-layout) (Arch Linux)

```bash 
# e.g.
yay -Sy && yay -S hyprland-per-window-layout
```

Add to hyprland.conf:
```
exec-once = /usr/bin/hyprland-per-window-layout
```

### From Cargo

```bash
cargo install hyprland-per-window-layout
```

Add to hyprland.conf:
```
exec-once = ~/.cargo/bin/hyprland-per-window-layout
```

### Gentoo

Activate wayland overlay as described in [README](https://github.com/bsd-ac/wayland-desktop#activate-overlay-via-eselect-repository), allow **~amd64** keyword and then install it:

```bash
# emerge --ask gui-apps/hyprland-per-window-layout
```

### From Source

```bash
git clone https://github.com/coffebar/hyprland-per-window-layout.git
cd hyprland-per-window-layout
cargo build --release
mkdir -p ~/.local/bin/
cp target/release/hyprland-per-window-layout ~/.local/bin/
```

Add to hyprland.conf:
```
exec-once = ~/.local/bin/hyprland-per-window-layout
```

## Configuration

Optional. See [configuration.md](configuration.md) for setting default layouts per application.

Tested on Hyprland v0.50.
