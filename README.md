# dip-n-dotfiles

Use this repo with [chezmoi](https://www.chezmoi.io/) to track and reapply your dotfiles on fresh installs.

## First-time setup

1. Install chezmoi (pick your platform):
   - macOS (Homebrew): `brew install chezmoi`
   - Linux (script): `sh -c "$(curl -fsLS get.chezmoi.io)"`
2. Initialize this repo as your source state:
   - `chezmoi init https://github.com/grepmykeys/dip-n-dotfiles.git`
3. Add the dotfiles you want to keep (especially from `~/.config`):
   - Before you add anything, double-check it doesn’t include secrets (tokens, API keys, private keys). Consider `chezmoi add --encrypt` for sensitive files and/or `.chezmoiignore` to exclude them.
   - `chezmoi add ~/.zshrc`
   - `chezmoi add ~/.gitconfig`
   - `chezmoi add ~/.config/nvim`
   - `chezmoi add ~/.config/tmux`
   - Repeat `chezmoi add ~/.config/<app>` for each app you care about.
4. Review and apply:
   - `chezmoi diff`
   - `chezmoi apply`
5. Commit and push updates from the chezmoi source directory:
   - `chezmoi cd`
   - `git add . && git commit -m "Add initial dotfiles"`
   - `git push`

## Restore on a fresh machine

1. Install chezmoi.
2. Run:
   - `chezmoi init --apply git@github.com:grepmykeys/dip-n-dotfiles.git`
