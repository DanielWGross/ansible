1. Ensure Python 3 is installed.
    - I *think* this is the default for Mac but should confirm and update if necessary
2. Ensure Python 3 is in your `$PATH`
    - NOTE: Need to update with more specifics here.
3. Upgrade `pip`: 
    ```
    sudo pip3 install --upgrade pip
    ```
4. Install Ansible
    ```
    pip3 install ansible
```

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
