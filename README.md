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

## Installation

1. Ensure Apple's command line tools are installed (`xcode-select --install to launch the installer).
2. Ensure Python3 is installed by running `python3 --version`.
3. Add Python 3 to your $PATH

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
10. Clone this repo
11. Run the playbook with `ansible-playbook main.yml --ask-vault-pass --ask-become-pass`

12. Install System76 Keyboard Configurator

- https://system76.com/accessories/launch/download

13. Install Charmstone

- https://charmstone.app/

## Notes & TODOS

- Mac settings - Create a screenshot folder somewhere instead of dumping on desktop
- Make a streamdeck profile and then export it.
  - These could _probably_ just be vaulted, right?
- The .zshrc file, once "complete", should probably just be on github and then a task to copy it over to where it needs to go.
- The .nvm directory may need to be manually created after being installed with homebrew. Run `brew info nvm` for actual directions

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
- Discord:
  - Open the App
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
- Hey:

  - Open the App
  - Login

- Insomina:
  - Open the App
  - Login
- iTerm:

  - Profiles -> Other Actions -> Import JSON Profiles
  - Import the iterm_default_profile.json file

- Rectangle Pro:

  - Open the App
  - Add License Key (In backup_codes directory)

- SwitchResX
  - Open the App
  - Add License Key (In backup_codes directory)
- VSCode
  - Open the App
  - Enable Settings Sync

### Terminal System Settings:

- Disable press-and-hold for keys in favor of key repeat
- `defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false`

- Set a blazingly fast keyboard repeat rate
- `defaults write NSGlobalDomain KeyRepeat -int 1`
- `defaults write NSGlobalDomain InitialKeyRepeat -int 10`

### System Settings:

- System Settings -> Notifications
  - Turn Everything Off
- System Settings -> Siri & Spotlight
  - Turn Off "Ask Siri"
  - Uncheck all options under "Spotlight"
- System Settings -> Keyboard -> Keyboard Shortcuts -> Spotlight
  - Uncheck "Show Spotlight Search"
  - Uncheck "Show Finder search window"

NOTE: Can use `ansible-vault encrypt_string '<string_to_encrypt' --name '<string_name_of_variable>'`
NOTE: Can use `ansible-vault encrypt <file>`

TODO:

- Config iTerm
- Config Oh My Zsh
- Config Karabiner Elements
- Take Current Config & Add to Ansible
  - Make a task to copy to ~/.config/karabiner/
- Config Rectangle Pro
  - Make a task to copy to ~/Library/Application Support/Rectangle Pro/RectangleProConfig.json
- Config Tmux
