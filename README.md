# macOS
My personal macOS files settings and scripts.

We are going to manage our packages using `brew` or other console commands whenever it's possible.

## Requirements


### Install Homebrew

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

You might want to check if brew was correctly installed using `brew doctor`.


### Install Homebrew Cask

```bash
brew tap caskroom/cask
```

### Install some cool stuff

Make sure to read what you're installing:

```bash
brew cask install iterm2 sublime-text github-desktop sequel-pro vlc transmission  firefox google-chrome
```

### Install Source Code Pro font 

Download, extract and open with `Font Book` app:
[Adobe Source Code Pro (zip)](https://github.com/adobe-fonts/source-code-pro/archive/2.030R-ro/1.050R-it.zip)


## TODO:
- terminal colors
- pappermint color pallete.
- .bash_profile
- python3 
- brew autocomplete
