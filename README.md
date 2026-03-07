# Dotfiles

Personal dev environment: wezterm + zsh + tmux + neovim.

## New Mac Setup

```bash
# 1. Install Xcode Command Line Tools
xcode-select --install

# 2. Clone this repo
git clone https://github.com/ce20480/dotfiles.git ~/dotfiles

# 3. Run setup
cd ~/dotfiles && chmod +x setup.sh && ./setup.sh

# 4. Restart terminal. Open Wezterm.

# 5. Authenticate GitHub
gh auth login

# 6. Generate SSH key
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
# Add to GitHub: Settings > SSH and GPG keys > New SSH key

# 7. Set git identity
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"

# 8. Set up Raycast
# Open Raycast > Set hotkey to Cmd+Space
# System Settings > Keyboard > Keyboard Shortcuts > Spotlight > uncheck both
```

## What's Included

| Category | Tools |
|----------|-------|
| Terminal | Wezterm (GPU-accelerated, Lua config) |
| Shell | Zsh + Powerlevel10k + autosuggestions + syntax highlighting |
| Editor | Neovim ([ce20480/nvim](https://github.com/ce20480/nvim)) |
| Multiplexer | tmux ([ce20480/Tmux](https://github.com/ce20480/Tmux)) |
| CLI | eza, zoxide, fzf, yazi, ripgrep, lazygit, jq |
| Languages | pyenv (Python), fnm (Node), uv |
| Dev | awscli, libpq (psql), gh, OrbStack |
| Apps | Raycast (Spotlight replacement) |

## What setup.sh Does

1. Installs Homebrew
2. Installs all packages from Brewfile
3. Symlinks configs (.zshrc, .wezterm.lua, .p10k.zsh, .zshenv) to home directory
4. Clones nvim + tmux configs
5. Installs Node LTS via fnm + yarn
6. Installs Python 3.13 via pyenv
7. Creates SSH config (agent persistence with macOS Keychain)
8. Sets git defaults (default branch: main, editor: nvim)

## Machine-Specific Overrides

Create `~/.zshrc.local` for anything specific to one machine (not committed):

```bash
# Example: work-specific settings
export SOME_API_KEY="value"
alias myalias="/path/to/script.sh"
```

## SSH

setup.sh creates `~/.ssh/config` with agent persistence so you only need to enter your key passphrase once per reboot (stored in macOS Keychain).
