# My dotfiles
This repository contains the dotfiles for my personal system (macOS). Managed using [Stow](http://www.gnu.org/software/stow/). Shell choice is `zsh`. Terminal emulator is Iterm2.

## Note
I used to force myself to learn all fancy dotfile config or automated process, but then realize that it wasn't worth the time for trial. Getting a minimal setup and install step by step is the way (inspired by [@dreamsofautonomy's zensh config](https://www.youtube.com/watch?v=ud7YxC33Z3w&t=237s))

## Requirements
Ensure to have the following installed on the system:
- [Homebrew](https://brew.sh/)
- [Iterm2](https://iterm2.com)
- [Stow](http://www.gnu.org/software/stow/) (using homebrew)

## Setup
Clone the repository, navigate to the folder and follow the steps as follows:

### Homebrew bundle
Use the follow command to install some packages listed in `homebrew/.Brewfile`:
```
brew bundle --file=~/.dotfiles/homebrew/.Brewfile
```

### Stow for dotfiles management
Within the cloned folder, run `stow .`. This will create all symlinks to your home directory. Create a new terminal to refresh everything and follow some setup instructions (if any).

### Plugins
- Plugin manager: Zinit (https://github.com/zdharma-continuum/zinit)
- Font: JetbrainsMono Nerd Font (https://www.nerdfonts.com/font-downloads)
- Prompt: Powerlevel10k (https://github.com/romkatv/powerlevel10k)
- zsh-syntax-highlighting
- zsh-completions
- zsh-autosuggestions
- fzf-tab

### Favorite themes
- Catppuccin Macchiato
- Tokyo Night
