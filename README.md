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

```zsh
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

## DS environment setup
Package manager: Miniconda.

Create dedicated environment for jupyter:

```zsh
conda create -n jupyter_env -c conda-forge --override-channels -f ~/.dotfiles/conda_minimal_requirement.txt
```

To host a service that auto start the JupyterLab, create a filed name `jupyter.plist` in `~/Library/LaunchAgents` and fill the file with this setting:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
   <key>Label</key>
   <string>jupyter-startup</string>
   <key>ProgramArguments</key>
   <array>
      <string>/opt/homebrew/Caskroom/miniconda/base/envs/jupyter_env/bin/jupyter</string>
      <string>lab</string>
      <string>--no-browser</string>
   </array>
   <key>WorkingDirectory</key>
   <string>/Users/<username></string>
   <key>RunAtLoad</key>
   <true/>
   <key>StandardOutPath</key>
   <string>/Users/<username>/Library/Logs/jupyter.log</string>
   <key>StandardErrorPath</key>
   <string>/Users/<username>/Library/Logs/jupyter.log</string>
</dict>
</plist>
```
Then activate the service with:

```zsh
launchctl load ~/Library/LaunchAgents/jupyter.plist
```
To deactivate the service:

```zsh
launchctl unload ~/Library/LaunchAgents/jupyter.plist
```

Create new kernel: 

```zsh
python -m ipykernel install --user --name <kernel-name>
```

For running notebooks in VSCode, it is much simpler, just remember to install `ipykernel` within it, then when select the kernel, choose the environment name that we have created. 




























