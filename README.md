# screen_ssh
Simple script to setup an SSH through a screen

## Usage
```bash
sshc -n [name_of_screen] -s [ssh server name/ip] 
```
OR
```bash
sshc [ssh server name]
```

## Setup
To make it easier, set up a permanent SSH key with the upstream server for passwordless login.
E.g.
```bash
ssh-keygen (generate your own keys)
ssh-copy-id [destination SSH server]
```

Then edit your SSH config (~/.ssh/config)
```bash
Host [server alias name]
  hostname [server ip]
  user [your username]
  port [SSH port, usually 22]
```
