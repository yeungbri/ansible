# Prereqs
Homebrew
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`
Ansible
`brew install ansible`
Install roles/collections
`ansible-galaxy install -r requirements.yml`

---

# Ansible
roles make our tasks reusable
I could just include a playbook, but you can run an entire role or break apart your setup setup into multiple roles.

`ansible-playbook main.yml --ask-become-pass`

## Organization
https://github.com/bradwilson/ansible-dev-pc
Each role installs and configures a category of use cases or just one single use case.
Each task yml file is essentially a play to install/configure a specific use case or a piece of the use case.

The idea is to separate out the tasks into chunks that can be easily installed/omitted.
For example, if I choose to switch out nvim for something other editor, I can simply not include that role anymore.
This will break down for shared dependencies.

---

Steps to setup on a new macos:

# Install applications
(via homebrew)

# OSX
## Keyboard
- [x] Remap the caps lock key to escape
## Dock
- [x] Order applications
- [x] Set dock settings
## Trackpad
- [?] Trackpad scroll direction
- [?] Tap to click
## Displays
- [x] Turn on Nighshift
## Menu bar
- [?] Always show date
- [?] Remove spotlight icon
## Ricing
- [ ] Install desktop backgrounds

# Window Management
## Rectangle
(manual) Enable security permissions
- [?] Configure settings: Hide menu bar icon

## Quicksilver
(manual) Enable security permissions
- [ ] Setup triggers for each application
  - [ ] See if replacing these files works:
  https://github.com/quicksilver/Quicksilver
  ```
  ~/Library/Application Support/Quicksilver
  ~/Library/Caches/Quicksilver
  ~/Library/Preferences/com.blacktree.Quicksilver.plist
  ```

# Browser
## Chrome
- [x] Install extensions
- [ ] Configure settings
    Reopen tabs on close
    Homepage: new tab

---

Development

# Dotfiles
- [ ] yadm

# git
- [x] Create new ssh key for machine
- [ ] Configure global git settings - yadm?
- [ ] Pre-commit hook?

# Terminal
## iterm2
- [ ] Configure iterm2 to work
## zsh
- [x] Install Antigen
  Antigen is invoked inside your `~/.zshrc`
- [x] Install plugins
- [x] Install Starship
  1. Install nerdfont
  2. brew install starship
  3. Add `eval "$(starship init zsh)"` to the end of your zshrc
  4. Configure starship: https://starship.rs/config/

# IDE
## VSCode
- [ ] Configure VSCode
- [?] Install extensions

## Neovim
- [ ] Configure Nvim
- [ ] Setup tmux
