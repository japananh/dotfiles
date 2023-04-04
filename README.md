# Dotfiles

Life is short so I spend my time to manage dotfiles.

## Requirements

This dotfiles are managed by [chezmoi](https://www.chezmoi.io). You must install chezmoi to run this project.

* Note: chezmoi (sei-moi) is a French word, meaning "at my house".

```bash
# Install chezmoi with homebrew
brew install chezmoi
```

## Command overview

- Command overview: https://www.chezmoi.io/user-guide/command-overview/

- Add files to chezmoi

```bash
# Encrypt a file
chezmoi add --encrypt ~/.ssh/config

# Edit a file, run apply afterwards
# Default editor in chezmoi is vim
chezmoi edit --apply ~/.ssh/config
chezmoi edit ~/.ssh/config

# Update dotfiles from the source directory
chezmoi apply
```

- Push config to Github

```bash
# Open a shell in the source directory
chezmoi cd

# Run `git` in the source directory and pass extra args to the command
# Need `--` to prevent chezmoi from consuming these args
chezmoi git -- commit -m "feat: update dotfiles"
```

- Templating

```bash
# Edit config 
chezmoi edit-config

# Add new config
[data]
    email = "email"
    name = "name"

# Add a file as a template
chezmoi add -T --template ~/.gitconfig

# If a file already managed by chezmoi, but not a template
chezmoi chattr +template ~/.zshrc

# Update `~/.gitconfig` file using template as below
[user]
    email = "{{ .email }}"
    name = "{{ .name }}"
```
