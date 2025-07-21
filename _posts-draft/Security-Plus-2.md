22% of the exam

## 2.1

### Threat Actors
* Essentially anybody for any reason /:
* **Advanced Persistent Threat (APT)** - Constant attacks with massive resources
* **Hactivist** a hacker with a purpose
* Insider Threat
* Shadow IT - works around the internal IT organization and builds their own infrastructure

## 2.2 

### Threat Vectors
* Method used by the Attacker also called "Attack Vectors"
* **Message Based Vectors** - first and one of biggest because everyone has at least on messaging systems "Phishing" - fake link
* **Image based Vectors**- using the image formats like .SVG which is described in XML for HTML injections and shit
* **FIle based Vectors** - PDFs are succeptible ZIPS are easy af
* **Voice call vectors** - India
* **Removable Device Vectors** - USBs
* **Vulnerable Software Vector** 
* **Unsupported Systems Vectors**
* **Unsecure Network Vectors** - Default credentials is a good way to get access
* **Supply Chain Vector** - Tamper with the infrsatructure like repairing installing or after installation

### Phishing & Impersonation
* typosquatting - messing with the URL
* Pretexting - lying to get information
* Vishing - Voice fishing (think about what accent that is hmmmmmmm Indi*)

### Watering Hole Attack
* They do research what sites you might visit, industry related or the sandwhich shop type shit yk. U never know. It infects all visitors but theyre waiting for u. 
* Defense in depth. 

## 2.3

### Memory Injections
* Malware runs in memory usually on common process that runs and in running that process u run the malware
* DLL-injection , Dynamic Link Library is most common 

### Buffer Overflow Attack
* Writes more than what is expected into a specific memory so that it overflows seeing if they can change the way it works

### Race Condition
* 2 conditions happen at the same time when the developers werent prepared for it
* TOCTOU Time of check to time of use attack.

### Malicious Updates
* updating is lies

### Operating Systems
* Keep your operating system up to date

### SQL Injection
* Structured Query Language SQL
* Database management question to gain information
* UserName

### Cross site scripting
* XSS
* Security Vulnerability in browser
* INformation from one site shared with another site "cookies" I think

    **None-persistent (reflected) SXX attack**
* Website allows scripts to run in user input
* Attacker emails a link that takes and it runs a script that sends credentials ids cookies to the attacker
    
    Persistent stored is a message on a social network and everyonde gets it.

### Hardware Vulnerabilities
* Most dont have accessible OS, they have Firmware
* Connected to the network
* EOL nottice, end of life that Manufacture stops selling a product, important for security patches and updates
* Legacy Platforms - older os, applications middleware that can be exploited or are at risk

### Virtualization Security
* Managing a clowd VMs are built and taken down constantly throughout the day. 

Virtualization Vulnerabilities 
1. Local Privilege Escalations
2. Command Injection
3. Information Disclosure

Shouldnt be possible to go on different VMs on the network, this is called a **VM Escape** iunteract with the host Operating system or hardware

**Resource Reuse** Because all the VMs share physical and virtual resources. Data can inadvertently be share as a result

### Cloud Specific Vulnerabilities
* DOS attack Denial of service attack. 
* Authentication bypass
* Directory traversal messing with the web
* Remote code execution

### Supply Chain Vulnerabilities
* Raw materials -> Suppliers -> Manufacturers -> Distributors -> Customers -> Consumers
* Service provider of security is poor

### Misconfiguration Vulnerabilities
* open permissions
* unsecured admin accounts
* Insecure protocols
* Default settings - Mirai botnet takes advantage of default configurations
* Open port

### Mobile Device Security
* Packed with sensative data always connected to the internet.
* Jailbreaking/rooting u can replace the OS, installs a custom firmware
* Sideloading, downloads that circumvent security to install manually 
* a malicious app "Tiktok" imo 

### Zero Day Vulnerabilities
 The next big vulnerability

 ## 2.4
 ### Malware
 * Ransomeware

 ### Virus
 * Malware thats able to reproduce itself and infect the computer or other computers
* Program Virus - apps
* Boot Sector Virus - OS
* Script Virus - OS and Browser
* Macro Virus
* Fileless virus -  stealth attack not written to a drive, it happens in the memory.

### Worms
* No user intervention needed
- Uses the network as a transmission medium
* Wannacry worm

### Spyware 
* spies on you surfing habits
* Keyloggers capture every keystroke and sends your keystrokes back to the attacker
* Also can log a bunch of other shit even your screen
* DarkComet-RAT Keylogger
* Malware Bytes
* Logic bomb - waits for a predefined event or time, difficult to identify, also difficult to recover. 

### Bloatware and Rootkit
- New computer phone includes bs apps usually payed to be included by the manufacturer.
* Unix root
* Hides in the kernel/os
* Secure Boot is the modern deterent and stops from malware infecting the pc.

### Physical Attack
* RFID cloning is everywhere
* Why we have MFA
* Environmental Attack (power is common

### Denial of Service
* DDOS - Distributed Denial of service
* botents, thousands or millions of computers at command. Zeus botnet infected over 3.6 million PCs
* DDoS reflection and amplification, so thats why if u request data to shut it down. 
* Runs on DNS for packet exchange you get alot more information than u give in a query

### DNS poisoning
* how i got hacked essentially
* Domain hijacking
* URL hijacking

### Wireless Attacks
* 802.11 management frames. Used to connect device and disconnect. 
* Very little security on these device frames (So cool)
* RF Jamming. Radio Frequency Jamming
* Wireless Jamming- Sends interfering wireless signals
* Data sent at random times to mess up debugging
* REactive jamming - only when someone else tries to communicate
* Needs to be close to be effective
* Fox hunting, hunt down teh jam, need a directional antenna, attenuator

### On Path Attacks.
* Man in the middle attack
* Watch without you knowing 
* ARP poisoning, on path attack on the local IP subnet
