# macOS
My personal macOS files settings and scripts.

We are going to manage our packages using `brew` or other console commands whenever it's possible.

## Requirements

### Install Homebrew

Ref: [https://brew.sh](https://brew.sh)

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

You might want to check if brew was correctly installed using `brew doctor`.


### Install Homebrew Cask

Ref: [https://caskroom.github.io](https://caskroom.github.io)

```bash
$ brew tap caskroom/cask
```

### Install some cool stuff

Pick just what you need:

### SysAdmin stuff
```bash
$ brew cask install iterm2
```
#### Dev stuff
```bash
$ brew cask install sublime-text github-desktop sequel-pro firefox google-chrome
```
#### Audio/Video Stuff
```bash
$ brew cask install vlc transmission spotify
```

### Social Stuff
```bash
$ brew cask install telegram skype whatsapp
```


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


## Sublime Text 3

A general set up for day to day using.

### Install Package Control

On latest builds you shoud easly install _Package Control_ through main menu. On 3126 build:
 `Tools` -> `Install Package Control...`

After a couple seconds you shoud see a _successfully installed_ message.

### Installing Packages

Now we are able to hit `Cmd` + `Shift` + `P` keys and look for `Package Control: Install Package`, then install these two packages:

- `Theme - SoDa Reloaded`
- `Monokai - SpaceGray`

### User Settings

With those two packages installed we can change the sublime user settings.

You can use my [Sublime Settings](https://github.com/RodrigoJimmy/macOS/blob/master/files/Preferences.sublime-settings) as a starting point.


## Terminal and iTerm2 colors

In order to enable colors in macOS terminal and iTerm2 you must have the `Colorful Terminal` block of [my .bash_profile](https://github.com/RodrigoJimmy/macOS/blob/master/files/bash_profile) on your own `~/.bash_profile` file.
I don't know about you, but I do like a colorful terminal.

### Peppermint color scheme

You should try peppermint color theme [for iTerm2](https://raw.githubusercontent.com/dotzero/iTerm-2-Peppermint/master/Peppermint.itermcolors) or [for terminal](https://noahfrederick.com/get/Peppermint.1.2.terminal.zip).

Ref:
- [Peppermint for terminal](https://noahfrederick.com/log/lion-terminal-theme-peppermint.html)
- [Peppermint for iTerm2](https://github.com/dotzero/iTerm-2-Peppermint)

I personally like `SF Mono`, `Source Code Pro`, `Monaco`, and `Menlo` fonts, on this order and size `11`.

You can get the Adobe Source Code Pro font [here](https://github.com/adobe-fonts/source-code-pro/archive/2.030R-ro/1.050R-it.zip).

Download and extract, then install with `Font Book` app.


## Python Development Environment

MacOS comes with Python 2.7, so I'm going to install Python3 using brew and show how simple is to get started working with venvs on Python3:


### Install python3

```bash
$ brew tap homebrew/core
$ brew install python3
$ pip3 install --upgrade pip setuptools wheel
```

### Create a common virtual env area

```bash
$ mkdir -p ~/Code/python3_envs
```

### Creating a django project for instance

First we have to create our virtual environment.
ref: [https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html)

```bash
# create the virtual environment
$ python3 -m venv ~/Code/python3_envs/projectX

# load the venv
$ source ~/Code/python3_envs/projectX/bin/activate
# after issue the command above you should see
# (projectX) prefixing your command prompt
# alternatively might run pip --version or python --version
(projectX) $ python --version
Python 3.6.1
(projectX) $ deactivate
$ python --version
Python 2.7.10
```

Now we are able to install and create a new Django 1.11 project inside projectX python virtual environment.

```bash
# activate your django venv
$ source ~/Code/python3_envs/projectX/bin/activate
(projectX) $ cd ~/Code
(projectX) $ pip install django
(projectX) $ django-admin startproject projectX
(projectX) $ pip freeze  > requirements.txt
(projectX) $ ./manage.py runserver

# do some work
(projectX) $ exit
```
