# MacOS Settings and Installation

## System Preferences

First, update MacOS to the most recent version. Go to **Apple Menu > About This Mac > Software Update.**

### Users & Groups

* Setup Password, AppleID, App Store, iCloud, Find my Mac, etc.

### General

* Appearance
  * Change appearance to *Dark*

### Dock

* Position on Screen > *Left*
* Enable *Minimise windows into application icon*

### Siri

* Disable *Enable Ask Siri*

### Language & Region

* Change primary language to *English*

### Security & Privacy

* Require password *immediately* after sleep or screen saver begins
* Enable *FileVault*
* Enable *Firewall*

### Trackpad

* Point & Click
  * Enable *Tap to click*
* Scroll & Zoom
  * Disable *Natural* Scroll direction

### Keyboard

* Touch Bar shows *App Controls* (also check *Show Control Strip)
* Press Fn key to *Show F1, F2, etc. Keys*
  
### Date & Time

* *Show date* in menubar
  
### Finder

* General
  * Change *New finder windows show* to your home directory
* Sidebar
  * Add *Home* and *Programming* directory
  * Uncheck *Recents*, *Airdrop*, *Movies*, *Music*, and *iCloud Drive*
* Advanced
  * Enable *Show all filename extensions*

### Other

* Change *default folder for screenshots*
  * Create folder *Screenshots* inside *Pictures* to store screenshots
  * Run following commmand: `defaults write com.apple.screencapture location /Users/USERNAME/Pictures/Screenshots/`

### Menubar

* Remove *Display*
* Change Battery to *Show percentage*

## XCode

* Install **XCode** from the [Apple Developer Website](https://developer.apple.com/download/applications/). This will include the *XCode Command Line Tools* necessary for compiling SDKs and applications.

## Homebrew

Homebrew is *the missing package manager for MacOS* and it is essential for anyone who aspires to be a developer. You need the *XCode Command Line Tools* to run Homebrew, which also include compilers and other tools to build from source. You can install the *Command Line Tools for XCode* by running the following command:

```
sudo xcode-select --install
```
OR install *Command Line Tools for XCode* by going to https://developer.apple.com/download/more/?=command%20line%20tools. You'll be asked for your Apple Developer login during the install process.

Next, install Homebrew by following the installation instructions from the [Homebrew homepage](https://brew.sh/ "Homebrew Homepage") and copy the Homebrew installation command to your terminal.

After Homebrew is installed, restart your terminal and make sure everything is working by running:

```
brew doctor
```
If everything has been installed correctly, you'll be greeted with the message `ready to brew!`

## iTerm2

Use Homebrew to download and install iTerm2:

```
brew cask install iterm2
```

### Customization

* Change font size to 14pt
* Add following shortcuts to the Keyboard shortcuts:

| shortcut |	action	| Esc+ |
|----------|--------|------|
| ⌘←	| Send Escape Sequence	| OH |
| ⌘→	| Send Escape Sequence	| OF |
| ⌥←	| Send Escape Sequence	| b |
| ⌥→	| Send Escape Sequence	| f |

## Z-Shell

Use Homebrew to download and install the most recent version of `zsh`:

```
brew install zsh
```
To make `zsh` the default shell of **iTerm2** open *Preferences* > *Profiles* > *General* > *Command:* /usr/local/bin/zsh (this is the default location of `zsh` installed & managed by **Homebrew**).

The configuration file for `zsh` is called `.zshrc` and lives in your home folder at `~/.zshrc`.

## Oh My Zsh

Install Oh My Zsh by running the installation instructions found on the [Oh My Zsh GitHub Repo](https://github.com/robbyrussell/oh-my-zsh).

### Theme

Powerlevel10K is a really great theme for `zsh`. Install:

```
brew install romkatv/powerlevel10k/powerlevel10k
```

After installation, add the theme to your `.zshrc` file by running:
```
echo 'source /usr/local/opt/powerlevel10k/powerlevel10k.zsh-theme' >> ~/.zshrc
```

Restart `zsh` to initialize the Powerlevel10K theme. Type `p10k configure` if the configuration wizard doesn't start automatically.

### Plugins

Enable plugins:

```
plugins=(
  git
  brew
  colorize
  docker
  docker-compose
  jsontools
  node
  osx
  pip
  python
  vscode
  )
```

#### Zsh-autosuggestions

To enable autosuggestions, run:

```
brew install zsh-autosuggestions
```

And add the following line to your `.zshrc` file:

```
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

#### Zsh-syntax-highlighting

To enable syntax highlighting, run:

```
brew install zsh-syntax-highlighting
```

And add the following line to your `.zshrc` file:

```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

## Git

The most popular version-control system. Install it by running:

```
brew install git
```
Check whether the brewed version of `Git` is used by the command line by running:

```
which git
```
Which should output `/usr/local/bin/git`.

Define your Git user by running:

```
git config --global user.name "Your Name Here"
git config --global user.email "youremail@youremail.com"
```

### HTTPS for GitHub (recommended)

Create a personal access token (recommended) to perform Git operations over HTTPS ([see official documentation here](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token).

### SSH for GitHub

[See the official documentation](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh) on how to connect to GitHub using SSH keys.

## Tree

`tree` is a recursive directory listing command that produces a indented list of files of your current directory.

To install the latest version, run:

```
brew install tree
```

## Python

Although macOS already comes with Python installed, you don't want to mess with the system Python. Therefore, you need to install your own version(s). My recommended ways to install Python on macOS are:

1. Homebrew
2. Pyenv

### Homebrew Method
Python 3 is the default version when installing via Homebrew by running:

```
brew install python
```

Executable scripts from Python packages you install will reside in `/usr/local/share/python`, add this to your `PATH`.

### Pyenv Method

`pyenv` is a Python version manager that can manage and install different versions of Python on one system. This is especially helpful when you need to test your code against several Python versions, or when you work with different Python versions in different projects.

To install `pyenv` using Homebrew, run:

```
brew install pyenv
```

`pyenv` works by inserting a directory of *shims* in front of your standard `PATH`. Therefore, add `pyenv init` to your shell to enable shims and automcompletion. Make sure it is placed towards the end of the shell configuration file since it manipulates `PATH` during initialization.

```
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```

Restart your shell so the path changes take effect. You can check your path changes by running:

```
echo $PATH
```

It should include `"$(pyenv init -)"`. To update pyenv in the future, use:

```
brew upgrade pyenv
```

Instead of `install`. You can check out all the available versions of Python by running:

```
pyenv install --list
```

Subsequently, install the desired Python versions, for example:

```
pyenv install 3.5.2
```

The above command will install Python version 3.5.2. All installed Python versions are located in `~/.pyenv/versions`.

## Visual Studio Code

Best editor, no questions asked. Install by running:

```
brew cask install visual-studio-code
```

After that, you can launch VS Code from the terminal / iTerm2 with:
* `code .` will open VS Code in the current directory
* `code myfile.txt` will open `myfile.txt` in VS Code in the current directory

### Useful Extensions
* Python
* R
* ESLint
* Prettier
* Markdown preview
* GitLens
* Docker
* Paste JSON as Code


