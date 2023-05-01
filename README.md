## Introduction

This playbook is heavily inspired by others out there to create something that made sense for me. Few resouces I used along the way...

- [Jeff Geerling Mac Dev Playbook](https://github.com/geerlingguy/mac-dev-playbook)
- [The Primeagen Ansible Setup](https://github.com/ThePrimeagen/ansible)
- [Ansible MacOS Homebrew Packages Task](https://gist.github.com/mrlesmithjr/f3c15fdd53020a71f55c2032b8be2eda)
- [swyx New Mac Setup - Non-Ansible](https://www.swyx.io/new-mac-setup-2021)
- [Robin Wieruch Mac Setup - Non-Ansible](https://www.robinwieruch.de/mac-setup-web-development/)
- [Mina Markham Formation - Non-Ansible](https://github.com/minamarkham/formation)

## Installation

1. Ensure Apple's command line tools are installed (`xcode-select --install to launch the installer).
2. Ensure Python3 is installed by running `python3 --version`. 
3. Add Python 3 to your $PATH
  - Create a `.zshrc` in the root directory and add the following line:
    - `export PAATH=$HOME/Library/Python/3.9/bin:$PATH`
    - NOTE: You may need to confirm the path and version.
4. Ensure `pip` is available by running `python3 -m pip -V`.
5. Install Ansible by running `python3 -m pip install ansible`
6. Confirm Ansible installation by running `ansible --version`
















NOTE: Can use `ansible-vault encrypt_string '<string_to_encrypt' --name '<string_name_of_variable>'`

TODO:
- Use NVM to install Node
  - Need LTS
  - Need Whatever Guru Uses
- Config NVChad
- Config iTerm
- Config Karabiner Elements
- Take Current Config & Add to Ansible
  - Make a task to copy to ~/.config/karabiner/
- Config Rectangle Pro
  - Make a task to copy to ~/Library/Application Support/Rectangle Pro/RectangleProConfig.json
- Config Tmux
