# macOS

## macOS without root user&#x20;

When working on company hardware you are probably using it without administrative access. Let's make it as smooth as possible.

### **brew casks**

Brew does not require root privileges by design! If you installed brew with admin rights and then lost permissions you need to update your cask folder! This also happens when ITS installs brew for you. To change the default homebrew cask directory use this command:

```
echo "export HOMEBREW_CASK_OPTS=\"--appdir=$HOME/Applications\"" >> $HOME/.zshrc
```

Change `.zshrc` for other shells i.e. bash - `.bashrc`

You will need to reinstall cask if any already installed with root privileges:

```
brew remove name --cask
brew install name --cask
```

## Audio problems <a href="#audio-problems" id="audio-problems"></a>

When you have any problems with sound output, kill core audio service:

`sudo killall coreaudiod && sudo killall ControlStrip`

## Battery draining during sleep problems <a href="#battery-draining-during-sleep-problems" id="battery-draining-during-sleep-problems"></a>

To help you debug what is waking up your system during sleep check use:

`pmset -g log|grep -e " Sleep " -e " Wake "`

## Can't access Keychain after password change <a href="#cant-access-keychain-after-password-change" id="cant-access-keychain-after-password-change"></a>

Good password policy requires you to rotate your passwords in every few months.

_Never use the same password within few months._

If you have problems with keychain access, do not remove it yet! Some old password could work. If your password had a pattern -> try to use [https://github.com/ziman/keychain-bruteforce](https://github.com/ziman/keychain-bruteforce)

_Yet it's always better to use password manager with random passwords!_

## Terminal slow startup <a href="#terminal-slow-startup" id="terminal-slow-startup"></a>

Remove user logs.

`sudo rm /private/var/log/asl/*.asl`

## Short on disk space <a href="#short-on-disk-space" id="short-on-disk-space"></a>

Remember to clear your old brew junk, from time to time:

`brew update && brew cleanup`

If You're using Jetbrains Toolkit uncheck "Keep previous versions of tools to enable instant rollback"
