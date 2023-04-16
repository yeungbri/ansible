# Prereqs
Homebrew
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`
Ansible
`brew install ansible`

---

# Ansible
roles make our tasks reusable
I could just include a playbook, but you can run an entire role or break apart your setup setup into multiple roles.

ansible-playbook main.yml

You have to run
`ansible-galaxy install -r requirements.yml`

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

# Window Management
## Rectangle
Enable security permissions
Hide menu bar icon

## Quicksilver
Enable security permissions
Setup triggers for each application
- [ ] See if replacing these files works:
https://github.com/quicksilver/Quicksilver
```
~/Library/Application Support/Quicksilver
~/Library/Caches/Quicksilver
~/Library/Preferences/com.blacktree.Quicksilver.plist
```

# OSX
Remap the caps lock key to escape
Trackpad scroll direction
## Dock

# Browser
## Chrome
