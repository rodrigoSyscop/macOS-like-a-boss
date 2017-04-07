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


## SSH Key Pairs

If you need/want to create a new ssh key pair:

```bash
$ ssh-keygen -t rsa -b 3072 -C "$(whoami)@$(hostname)-$(date +'%Y-%m-%d')"
```
Just confirm the default directory locations to put your new key pair and **use a secure passphrase**q.

> It is also possible to create your private key without a passphrase. While this can be convenient, you need to be aware of the associated risks. Without a passphrase, your private key will be stored on disk in an unencrypted form. Anyone who gains access to your private key file will then be able to assume your identity on any SSH server to which you connect using key-based authentication. Furthermore, without a passphrase, you must also trust the root user, as he can bypass file permissions and will be able to access your unencrypted private key file at any time.


Just in case you are like me and wants to change the passphrase from time to time:

```bash
$ ssh-keygen -f ~/.ssh/id_rsa -p
```

Every time you connect to a ssh server thats needs your key, you will be prompted to your passphrase. To avoid this, you can safely use an `ssh-agent`.
On macOS you just need to put `AddKeysToAgent yes` on your sshd agent config file `~/.ssh/config` (e.g.: [config](https://github.com/RodrigoJimmy/macOS/blob/master/files/ssh_config))

ref: https://wiki.archlinux.org/index.php/SSH_keys
