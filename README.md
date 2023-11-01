# CURRENTLY DOING:

- Mac settings - Create a screenshot folder somewhere instead of dumping on desktop

System Settings:

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

# NEXT TO DO:

- Look into Synergy by symless. symless.com
- Install Powerlevel 10k
  - https://github.com/romkatv/powerlevel10k
- Neovim Config
- Config Oh My Zsh
- Config Tmux
- The .zshrc file, once "complete", should probably just be on github and then a task to copy it over to where it needs to go.
- Export Stream Deck Config

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

## Installation

1. Ensure there are no pending software updates.
2. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
3. Ensure Python3 is installed by running `python3 --version`.
4. Add Python 3 to your $PATH

- Create a `.zshrc` in the root directory and add the following line:
  - `export PATH=$HOME/Library/Python/3.9/bin:$PATH`
  - NOTE: You may need to confirm the path and version.

4. Ensure the `ansible_python_interpreter` path is correct in the `inventory` file
5. Ensure `pip` is available by running `python3 -m pip -V`.
6. Install Ansible by running `python3 -m pip install ansible`
7. Confirm Ansible installation by running `ansible --version`
8. Install Homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

- NOTE: Double check the command by visiting `https://brew.sh/`

9. Take a look at the output in the terminal as there will be some steps listed under "Nest steps"
  - Add Homebrew to your PATH
  - Confirm install by running `brew help`
11. Clone this repo
12. Run the playbook with `ansible-playbook main.yml --ask-vault-pass --ask-become-pass`

13. Install System76 Keyboard Configurator

- https://system76.com/accessories/launch/download

13. Install Charmstone
14. DDPM install failed because of Rosetta 2 needed. Look into this.
  - `sudo softwareupdate --install-rosetta`

- https://charmstone.app/

## Mac Config:

### Apps:

- 1Password:
  - Open the App.
  - Use ansible-vault to decrypt the emergency kit and sign-in
- Alfred
  - Open the App
  - Not using Powerpacks (currently)
  - Configure MacOS Permissions prompts
  - Disable Spotlight Search
    - System Settings -> Keyboard -> Keyboard Shortcuts... -> Spotlight
      - Uncheck Show Spotlight Search
      - Uncheck Show Finder search window
  - Enable Alfred Hotkey -> Command + Space
- Arc:
  - Open the App
  - Login
  - Arc -> Set as Default Browser
  - Add 1Password Extension
- Charmstone
  - https://charmstone.app/
- Dell Display and Peripheral Manager
  - `ctrl` + `cmd` + `t`: Toggle Inputs (USB-C -> HDMI)
  - May not be necessary but double-check the firmware for the monitor to see if it can be upgraded
- Discord:
  - Open the App
 
- Elgato Camer Hub
  - Open the App
  - Set Zoom/FOV to 170%
  - Set Preview Format to 1080p60
     
- Elgato Facecam
  - Open the App
  - Update firmware
- Elgato Control Center
  - Preferences:
    - Enable Link Accessory Controls
    - Check for Updates
    - Enable Automatically check for updates
    - Enable Open automatically on Log In
- Elgato Wave Link:

  - Preferences:
    - Check for Updates

- Heroku:

  - Run `heroku update`
  - Run `heroku login`

- Hey:

  - Open the App
  - Login

- Insomina:
  - Open the App
  - Login
- iTerm:

  - Profiles -> Other Actions -> Import JSON Profiles
  - Import the iterm_default_profile.json file

- Loom
  - Open the App
  - Login with SSO
  - Enable all necessary permissions

- Rectangle Pro:
  - Open the App
  - Add License Key (In backup_codes directory)

- Slack
  - Login with 2U email address
  - Add current cohort Slack workspace and Pink Brain
  - Enter 2FA in Pink Brain

- SwitchResX
  - Open the App
  - Add License Key (In backup_codes directory)

- VSCode
  - Open the App
  - Enable Settings Sync
 
- Zoom
  - Open the App
  - Uncheck "Automatically keep Zoom desktop client up to date"
  - Login with 2U Zoom info
