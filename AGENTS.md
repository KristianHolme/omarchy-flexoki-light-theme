# AGENTS.md

## Cursor Cloud specific instructions

This repository is an **Omarchy theme** ("Flexoki Light"), not a software application. It is a
static collection of declarative theme/config files consumed by the [Omarchy](https://omarchy.org)
desktop (Hyprland/Arch based). There is **no source code, package manager, build system, test
suite, or dev server**.

### Files and what consumes them
- `colors.toml` — template source of truth for the palette (terminal/app colors); parsed as TOML.
- `btop.theme` — theme for the `btop` system monitor (`theme[...]="#RRGGBB"` entries).
- `walker.css` — GTK `@define-color` rules for the Walker launcher.
- `neovim.lua` — LazyVim plugin spec selecting the `flexoki-light` colorscheme.
- `vscode.json` — references the VSCode extension `shadesOfBuntu.flexoki-light`.
- `icons.theme`, `light.mode` — GNOME icon/light-mode references.
- `backgrounds/*.png`, `preview.png` — wallpapers and preview image.

### "Lint/test/build/run"
There are no project commands. The meaningful checks are validating that the config files are
well-formed and demonstrating the palette in a real consuming app:
- Validate `colors.toml`: `python3 -c "import tomllib; tomllib.load(open('colors.toml','rb'))"`.
- Validate `neovim.lua`: `luac5.4 -p neovim.lua` (requires `lua5.4`).
- Demonstrate the theme end-to-end with `btop` (requires `btop`, not part of this repo):
  copy `btop.theme` to `~/.config/btop/themes/flexoki-light.theme`, set
  `color_theme = "flexoki-light"` in `~/.config/btop/btop.conf`, then run `btop` in a terminal.

### Notes
- The full Omarchy theme install flow (`omarchy-theme-install`) is not available on this Ubuntu
  VM (Omarchy is Arch/Hyprland based); validate/demonstrate individual files instead.
- `btop` and `lua5.4` are demo/validation tools only — they are NOT project dependencies, so they
  are intentionally left out of the startup update script.
