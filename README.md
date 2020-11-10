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

* Install XCode from the App Store. This will include the *XCode Command Line Tools* necessary for compiling SDKs and applications.

## Homebrew

Homebrew is *The missing package manager for MacOS* and it is essential for anyone who aspires to be a developer. You need the *XCode Command Line Tools* to run Homebrew and they include compilers and other tools. You can install the *Command Line Tools for XCode* by running the following command:
```
sudo xcode-select --install
```
Next, install Homebrew by following the installation instructions from the [Homebrew homepage](https://brew.sh/ "Homebrew Homepage").

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
To make `zsh` the default shell of **iTerm2** open *Preferences* > *Profiles* > *General* > *Command:* /usr/local/bin/zsh (this is the default location of `zsh` installed & managed by Homebrew).
