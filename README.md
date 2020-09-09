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

I highly recommend you put this in your ~/.bashrc for your SSH server you're connecting to:
```bash
IGNOREEOF=10
```
This ensure that you do not accidently quit the bash session while trying to detach from the screen!

## Usage
```bash
sshc -n [name_of_screen] -s [ssh server name/ip] 
```
OR
```bash
sshc [ssh server name]
```

## Dependencies
bash
screen

## Useful commands
```
screen -ls              # Shows all your connections
CTRL + A + D            # Disconnect from current screen session
screen -r [screen name] # Connect to suspended screen session
```
