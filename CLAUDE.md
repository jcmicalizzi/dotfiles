# CLAUDE.md — dotfiles

Personal dotfiles for a Linux (Ubuntu) development environment, managed via Oh My Zsh and bootstrapped with `bootstrap.sh`.

## Repo Structure

- `de.zshrc` — the main zshrc; copied to `~/.zshrc` by bootstrap
- `bootstrap.sh` — idempotent setup script, run with `./bootstrap.sh`
- `Brewfile` — Homebrew packages
- `plugins/` — custom Oh My Zsh plugins, each in their own subdirectory
  - `de/` — personal utility functions and aliases (prefix: `de_`)
  - `claude_code/` — Claude Code aliases (prefix: `cc`)
  - `kona/` — k alias for the kona APL interpreter
  - `custom_azure/` — Azure-specific helpers
- `configs/` — config files copied to their target locations by bootstrap

## Conventions

- Custom aliases and functions go in `plugins/de/de.plugin.zsh`
- Claude Code-specific aliases go in `plugins/claude_code/claude_code.plugin.zsh`
- Function names in the `de` plugin use the `de_` prefix (e.g. `de_git_commit`)
- Claude Code aliases use the `cc` prefix (e.g. `ccr`, `ccp`)
- New plugins belong in `plugins/<name>/<name>.plugin.zsh` and must be added to the `plugins=(...)` list in `de.zshrc`
- After adding a plugin, register it in `de.zshrc` and it will be picked up by bootstrap automatically

## Bootstrap

Running `./bootstrap.sh` is idempotent and safe to re-run. It:
1. Pulls latest from `main`
2. Installs/updates Homebrew and packages from `Brewfile`
3. Copies `de.zshrc` → `~/.zshrc`
4. Copies all `plugins/*` → `~/.oh-my-zsh/custom/plugins/`
5. Copies configs to their target paths under `~/.config/`