# Mac M1 dotfiles with chezmoi

```bash
# Install chezmoi
brew install chezmoi
```

- Command overview: https://www.chezmoi.io/user-guide/command-overview/

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

- Push config to Github

```bash
# Open a shell in the source directory
chezmoi cd

# Run `git` in the source directory and pass extra args to the command
# Need `--` to prevent chezmoi from consuming these args
chezmoi git -- commit -m "feat: update dotfiles"
```

