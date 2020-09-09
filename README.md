# screen_ssh
Simple script to setup an SSH through a screen. 

## What is this for or how do I use this?
This is a script that I use to manage a home-based screen server, I've set up a RPi Zero W to manage all my screen sessions with this script. 
This keeps all my connections persistent, even if I turn off my own computer (RPi is very low power, so I can keep it on 24/7).

## Installation

Just drop the sshc script into your `~/local/bin/` and make sure to give it executable rights `chmod +x sshc`.

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


## Usage
```bash
sshc -n [name_of_screen] -s [ssh server name/ip] 
```
OR
```bash
sshc [ssh server name]
```
