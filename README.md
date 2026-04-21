# dotfiles

Personal configuration files managed with [GNU Stow](https://www.gnu.org/software/stow/).

This repository tracks a small set of terminal-focused tools and links them into `$HOME` with symlinks instead of copying files around.

## Contents

- Git configuration
- Kitty terminal configuration
- Yazi file manager configuration
- Powerlevel10k prompt configuration
- Kitty terminfo entries

## Repository Layout

This repository is organized by the final target paths under `$HOME`.

Examples:

- `.gitconfig`
- `.p10k.zsh`
- `.config/kitty/`
- `.config/yazi/`
- `.terminfo/`

That means this repository itself is treated as a single Stow package.

## Prerequisites

Required:

- `git`
- `stow`

Installed configurations may also expect these tools to exist:

- `zsh`
- `kitty`
- `yazi`
- `delta`
- `gh`
- Powerlevel10k
- a Nerd Font

## Installation

Clone the repository into your home directory:

```bash
git clone https://github.com/HuRuilizhen/dotfiles.git ~/dotfiles
```

Preview what Stow will do before creating symlinks:

```bash
cd ~
stow -nv dotfiles
```

If the preview looks correct, apply it:

```bash
cd ~
stow dotfiles
```

## Conflicts

If files already exist at the target paths, Stow will refuse to overwrite them.

Back up or remove conflicting files first, then run Stow again. For example:

```bash
mv ~/.gitconfig ~/.gitconfig.backup
mv ~/.config/kitty ~/.config/kitty.backup
```

Use `stow -nv dotfiles` again after resolving conflicts to verify the final plan.

## Updating

Pull the latest changes and re-run Stow:

```bash
cd ~/dotfiles
git pull
cd ~
stow dotfiles
```

## Uninstall

Remove the symlinks managed by this repository:

```bash
cd ~
stow -D dotfiles
```

This only removes symlinks created by Stow. It does not delete the repository itself.

## Notes

- This is a personal setup, not a universal bootstrap script.
- Some configuration choices assume macOS and a terminal-centric workflow.
- Secrets and machine-specific private files are intentionally not tracked here.
