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
  
### Date & Time

* *Show date* in menubar
  
### Finder

* General
  * Change *New finder windows show* home directory
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

* Install **XCode** from the App Store. This will include the *XCode Command Line Tools* necessary for compiling SDKs and applications.

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
echo 'source /usr/local/opt/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
```

Restart `zsh` to initialize the Powerlevel10K theme. Type `p10k configure` if the configuration wizard doesn't start automatically.

### Plugins

Enable plugins:
```
plugins=(
  git
  brew
  colorize
  osx
  pip
  python
  zsh-syntax-highlighting
  zsh-autosuggestions
  )
```

## Git

The most popular version-control system. Install it with:
```
brew install git
```

## Tree

`tree` is a recursive directory listing command that produces a depth  
