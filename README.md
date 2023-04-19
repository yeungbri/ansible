# Prereqs
Install Homebrew
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Install Ansible
`brew install ansible`

Install Ansible roles/collections
`ansible-galaxy install -r requirements.yml`

Run the playbook
`ansible-playbook main.yml`
`ansible-playbook main.yml --ask-become-pass`

---

# Ansible Notes
Task - Does one thing
Play - Runs a list of Tasks
Playbook - Contains multiple Plays
Role - shareable/reusable playbook (almost)
  You can call an entire role as one task, or even call roles inside of other roles
  `ansible-galaxy init role-name`
Collection - shareable group of modules/playbooks/roles/etc...
Ansible Galaxy - Where you share roles and collections

YAML
Jinja Templating - all the double curly brace stuff

Variables - exists on many layers, the closer to the task the higher precedence
Templates - to generate a templated file 

requirements.yml - defines role dependencies that get pulled via the ansible-galaxy command
main.yml - the main playbook to run with all the roles
ansible.cfg - defines which inventory file to use
inventory - a hosts file, ansible was designed to run against multiple nodes - but we are only using it for local macos setup

Each main.yml file in each role is the main "playbook" of the role. When you invoke a role, it runs that.

## Improvements
- [ ] More robust ansible tasks -> making use of checks/handlers/variables
  - [ ] For script tasks, write a check so it can be skipped if already configured (might not be worth the time)
- [ ] Usage of tags for more targetted installs
- [ ] Testing on a macos fresh VM
  https://mac.getutm.app/
- [ ] Look into ansible vault for secrets - not sure if I have any

---

# Project Organization
Philosophy: Keep tasks modular around a specific use case
Inspired by https://github.com/bradwilson/ansible-dev-pc
Pros:
- Makes things easy to find
- If you stop using a tool, you can remove it and all its config tasks in one place
  - Might want to write an uninstall task and comment out the rest of the file to deprecate though
Cons:
- Shared dependencies are tricky
- Lots of extra boiler plate to separate concerns even when they use the same tools (brew)

Philosophy: Ability to install the minimum necessary
If I'm setting up a mac but I don't intend to develop with Python, I don't need all the python tools
Or more dramatically, if I'm not doing dev work on the mac, then I don't need all my dev deps/installations

```
Dev tag - all dev env specific tools
Core tag - everything else I use on a mac
ansible-playbook main.yml --ask-become-pass --tags core 
ansible-playbook main.yml --ask-become-pass --tags dev

If you want to run a specific tag, use --start-at-task:
ansible-playbook main.yml --ask-become-pass --start-at-task "asdf"

Language specific installs
ansible-playbook main.yml --ask-become-pass --extra-vars "langs=[python,java]"
```

---

# Playbook Configurations
Try to track all the changes made by the playbook here.

## Install applications
Via homebrew, casks, or mac app store

## OSX Configuration
### Keyboard
- [x] Remap the caps lock key to escape
- [x] Don't add a period when you double space
#### Karabiner
- [ ] ctrl hjkl for arrow keys (still useful for builtin keyboards)
### Dock
- [x] Order applications
- [x] Set dock settings
### Trackpad
- [?] Trackpad scroll direction
- [?] Tap to click
### Displays
- [x] Turn on Nighshift
### Menu bar
- [?] Always show date
- [?] Remove spotlight icon
### Ricing
- [ ] Install desktop backgrounds

## Window Management
### Rectangle
(manual) Enable security permissions
- [?] Configure settings: Hide menu bar icon
### Quicksilver
(manual) Enable security permissions
- [ ] Setup triggers for each application
- [ ] See if replacing these files works:
https://github.com/quicksilver/Quicksilver
```
~/Library/Application Support/Quicksilver
~/Library/Caches/Quicksilver
~/Library/Preferences/com.blacktree.Quicksilver.plist
```

## Browser
### Chrome
- [x] Install extensions
Configure settings
- [ ] Reopen tabs on close
- [ ] Homepage: new tab
### Slack
- [ ] Sign into workspace

---

# Development Configuration
## Dotfiles
- [ ] yadm
- zshrc
- vscode settings/keybinds
- iterm2
- git config
- postman
- ssh config for different keys
- slack config

## git
- [x] Create new ssh key for machine
(manual) Add ssh key to github and/or gitlab

## Terminal
### zsh
- [x] Install Antigen
  Antigen is invoked inside your `~/.zshrc`
- [x] Install plugins
- [x] Install Starship
  1. Install nerdfont
  2. brew install starship
  3. Add `eval "$(starship init zsh)"` to the end of your zshrc
  4. Configure starship: https://starship.rs/config/
### iterm2

## IDE
### VSCode
- [?] Install extensions
### Neovim/Tmux

## Language/Tech Stack Specific
### Python
- [x] Install pyenv and pyenv-virtualenv
### Java

---
# Full Setup Steps
install brew + ansible
run ansible playbooks
  do the yadm steps as well
should be all configured