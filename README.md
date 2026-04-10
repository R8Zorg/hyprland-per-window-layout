# WARNING!
This repository is a modified version of an existing open-source project. It was recreated independently rather than forked in order to avoid directly linking to the original repository, whose contents include topics that may be subject to legal or regional restrictions.

The goal of this repository is purely technical: to adapt and improve the functionality of the original codebase for personal use. All modifications are focused on code, structure, and usability.

I want to make it clear that this decision is not directed against any individual, group, or viewpoint. I respect all people regardless of background, beliefs, or identity. The separation from the original repository is solely a precautionary measure to prevent potential legal or compliance issues in certain jurisdictions.

The project continues to follow the terms of the original MIT License, which is preserved in this repository.

If you are looking for the original work, please refer to its respective source.

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

### Only from Source

```bash
git clone https://github.com/R8Zorg/hyprland-per-window-layout.git
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

Optional. See [configuration.md](configuration.md) for setting default layouts per application. It also includes information on configuring **Waybar**


Tested on Hyprland v0.54.
