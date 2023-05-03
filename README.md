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



## Notes & TODOS
- Consider setting the default git config pull strategy to rebase
- When running the playbook there are a couple flags you may need...
  - `--ask-vault-pass` to provide your ansible vault password
  - `--ask-become-pass` to provide your system password (for sudo)











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
