
# NEXT TO DO:

- Mac settings - Create a screenshot folder somewhere instead of dumping on desktop
- Look into Warp (again)
- Install Powerlevel 10k
  - https://github.com/romkatv/powerlevel10k
- Neovim Config
- Config Oh My Zsh
- Config Tmux
    - https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/
    - https://sheerun.net/2014/03/21/how-to-boost-your-vim-productivity/
- The .zshrc file, once "complete", should probably just be on github and then a task to copy it over to where it needs to go.
- Export Stream Deck Config
- You Don't Need NERDTree - https://shapeshed.com/vim-netrw/

## Introduction

This playbook is heavily inspired by others out there to create something that made sense for me. Few resouces I used along the way...

- [Jeff Geerling Mac Dev Playbook](https://github.com/geerlingguy/mac-dev-playbook)
- [The Primeagen Ansible Setup](https://github.com/ThePrimeagen/ansible)
- [Ansible MacOS Homebrew Packages Task](https://gist.github.com/mrlesmithjr/f3c15fdd53020a71f55c2032b8be2eda)
- [swyx New Mac Setup - Non-Ansible](https://www.swyx.io/new-mac-setup-2021)
- [Robin Wieruch Mac Setup - Non-Ansible](https://www.robinwieruch.de/mac-setup-web-development/)
- [Mina Markham Formation - Non-Ansible](https://github.com/minamarkham/formation)

## Ansible Commands:

There are a few ansible commands that will be useful.

- `--ask-vault-pass` to provide your ansible vault password
- `--ask-become-pass` to provide your system password (for sudo)
- `-t` flag to run a specific tag such as: `-t nvm`
- `ansible-vault` to encrypt or decrypt files
  - Example: `ansible-vault encrypt_string '<string_to_encrypt' --name '<string_name_of_variable>'`
  - Example: `ansible-vault encrypt <file>`

## Pre-Install Setup

- System Settings -> Dock
  - Size - Medium
  - Magnification - Off
  - Position on screen - Right
  - Uncheck "Animate opening applications"
  - Uncheck "Show indicators for open applications"
  - Uncheck "Show suggested and recent apps in Dock"
  - Click wallpaper to reveal desktop - "Only in Stage Manager"
- System Settings -> Keyboard
  - Set Key repeat rate to "Fast"
  - Set Delay until repeat to "Short"
  - Change Shortcut to "Off"
  - Keyboard Shortcuts -> Spotlight
    - Uncheck "Show Spotlight Search"
    - Uncheck "Show Finder search window"
- System Settings -> Notifications
  - Turn Everything Off
- System Settings -> Siri & Spotlight
  - Turn Off "Ask Siri"
  - Uncheck all options under "Spotlight"
- Increase Key Repeat Faster than settings above
  - defaults write -g InitialKeyRepeat -int 10 # normal minimum is 15 (225 ms)
  - defaults write -g KeyRepeat -int 1 # normal minimum is 2 (30 ms)
  - NOTE: This settings won't take effect until you log out and then back in.

## Installation

1. Ensure there are no pending software updates.
2. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
3. Install Rosetta 2 (`sudo softwareupdate --install-rosetta`)
4. Ensure Python3 is installed by running `python3 --version`.
5. Create a `.zshrc` in the root directory and add the following line to add Python 3 to your PATH
  - `export PATH=$HOME/Library/Python/3.9/bin:$PATH`
  - NOTE: You may need to confirm the path and version.
6. Ensure the `ansible_python_interpreter` path is correct in the `inventory` file
7. Ensure `pip` is available by running `python3 -m pip -V`.
8. Install Ansible by running `python3 -m pip install ansible`
9. Confirm Ansible installation by running `ansible --version`
10. Install Homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
11. Add Homebrew to your PATH (See Next Steps from step above)
12. Confirm install by running `brew help`
13. Run the playbook with `ansible-playbook main.yml --ask-vault-pass --ask-become-pass`
14. Install [System76 Keyboard Configurator](https://system76.com/accessories/launch/download)
15. Install [Synergy](https://symless.com/synergy/download) 
16. Install [Charmstone](https://charmstone.app/)

## Mac Config:

### Apps:

#### 1Password:
  - Open the App.
  - Use ansible-vault to decrypt the emergency kit and sign-in

#### Alfred
  - Open the App
  - Not using Powerpacks (currently)
  - Configure MacOS Permissions prompts
  - Disable Spotlight Search
    - System Settings -> Keyboard -> Keyboard Shortcuts... -> Spotlight
      - Uncheck Show Spotlight Search
      - Uncheck Show Finder search window
  - Enable Alfred Hotkey -> Command + Space

#### Arc:
  - Open the App
  - Login
  - Arc -> Set as Default Browser
  - Add 1Password Extension

#### Charmstone
  - Configure based on the screenshot in the `screenshot` directory

#### Dell Display and Peripheral Manager (DDPM)
  - `ctrl` + `cmd` + `t`: Toggle Inputs (USB-C -> HDMI)
  - May not be necessary but double-check the firmware for the monitor to see if it can be upgraded

#### Discord:
  - Open the App

#### Elgato Camera Hub
  - Open the App
  - Set Zoom/FOV to 170%
  - Set Preview Format to 1080p60


#### Elgato Control Center
  - Open the App
  - Preferences:
    - Enable Link Accessory Controls
    - Check for Updates
    - Disable Automatically check for updates
    - Enable Open automatically on Log In

#### Elgato Stream Deck:
- Open the App
- Import Profile (Profile in this repo)

#### Elgato Wave Link:
  - Preferences:
    - Check for Updates

#### Heroku:
  - Run `heroku update`
  - Run `heroku login`

#### Hey:
  - Open the App
  - Login

#### Hyperkey
  - Open the App
  - Enable permissions
  - Set the following:
    - Enable "Remap physical key to hyper key: caps lock"
    - Disable "Quick press caps lock to execute"
    - Enable "Include shift in hyper key"
    - Uncheck all "Apply hyper key modifiers to keypress and:"
    - Enable "Launch on login"
    - Disable "Check for updates automatically"
    - Disable "Hide menu bar icon"

#### Insomina:
  - Open the App
  - Login with GitHub

#### iTerm:
  - Profiles -> Other Actions -> Import JSON Profiles
  - Import the iterm_default_profile.json file

#### MongoDB
  - Start MongoDB Server on System Startup
    - `brew services start mongodb/brew/mongodb-community`

#### MongoDB Compass
  - Open the App

#### Omnifocus
  - Open the App
  - General:
    - Quick Entry Shortcut: `Ctrl + Option + O`
    - Clippings Shortcut: `Hyper + O`
  - Style
    - Font size: Large
  - Notifications:
    - Set to "Alerts"
    - Enable everything
  - Badges:
    - Enable everything
  - Update
    - Uncheck "Check for updates"

#### Rectangle Pro:
  - Open the App
  - Enable permissions
  - Check "Launch Rectangle Pro on login"
  - Import Config (file in this repo)
  - Activate Rectangle Pro
    - Click "Purchase"
    - Click "Activate License"
    - Add Email - danwgross@gmail.com
    - Add License Key (In backup_codes directory)

#### Slack
  - Login with 2U email address
  - Add current cohort Slack workspace and Pink Brain
  - Enter 2FA in Pink Brain

#### SwitchResX
  - Open the App
  - Add License Key (In backup_codes directory)

#### VSCode
  - Open the App
  - Settings Sync:
    - Click "Backup and Sync Settings"
    - Click "Sign in"
    - Click "Sign in with GitHub"

#### Zoom
  - Open the App
  - Uncheck "Automatically keep Zoom desktop client up to date"
  - Login with 2U Zoom info
  - Make sure to check "Stay Signed in"
  - Settings:
    - General
      - Use dual monitors checked
  - System Preferences -> Privacy & Security -> Screen Recording -> Allow Zoom
  - System Preferences -> Keyboard Shortcuts -> Show/Hide Floating Meeting Controls
    - `Hyper+H`
    - Enable Global Shortcut
