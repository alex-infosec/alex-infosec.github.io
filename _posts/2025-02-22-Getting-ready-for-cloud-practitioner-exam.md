---
layout: post
title: "Pico Cybersecurity Primer"
subtitle: "Notes and First Impressions from the CTF Experience"
thumbnail-img: ./assets/img/ThePicoPrimer.png
tags: [CTF, Cybersecurity, TRX CTF 2025, Linux Threat Hunting, PicoCTF]
comments: true
mathjax: false
author: Alex Fluitt Martinez
---

# TRX CTF 2025
Fuck it were trying a CFT, yes I could finish that AWS certification, but ugh, not feeling it right now. I want to dive into cybersecurity nose, head, eyes open, first... I do not think Im going to finish 

## Signed up
This is what it looks like after signing up, btw my team name is alexinfosec (I know I know, origingal)
![CTF board](/assets/img/CTF board.png)
The event is in a jeapordy style, so each team I guess tries to complete as many of the challenges as possible

## My approach
Well since I have to go walk my dog soon, I have about 20 minutes to give a crack at one of these. I think Im only going to do the 50 point ones just to dip my toe in the water.

### (50 points) Online Python Editor
*If you're tired of fast and good-looking editors, try this. Now with extra crispiness!*

it comes to a link with the completed python editor website, I guess to test your code, and then the code files to try and do something. Im a little confused...

### AHHHHH
I was bashing my head against the wall. No luck in finding the flag. What I think Im going to do is watch some youtube videos on CTF's and see what they do and include the notes below

#### CTF for beginners | How to do CTF challenges ?? (AmanBytes)
1. He said To inspect element
2. He said to right click (View Page source)
3. burpsuite (tool used by cyber proffessionals to capture website requests)

He said to start with picoCTF, picoGym, picoPrimer

# PicoPrimer
## The Shell
"Understanding the shell can make or break one's ability to solve challenges in a CTF competition"
__CLI__ Command Line Interface

Having a cheat sheet with shell commands listed is a must for overcoming the challenge of memorizing commands

![CLI Cheat Sheet](./assets/img/CLI Cheat Sheet.png)

using TAB to tab complete


```bash
# the following command "parks" your shell in your home directory (which is
# somewhere you can create files!)
$ cd

# the following command shows where your shell is parked
$ pwd

# the following command creates a new directory called "tutorial" where you
# are currently parked
$ mkdir tutorial

# the following command moves your shell and parks it in the "tutorial" folder
# you just created
$ cd tutorial

# pwd stands for "print working directory". "working directory" is the
# technical term for where one's shell is parked
$ pwd

# the following command creates an empty file with the name "note.txt"
$ touch note.txt

# the following command lists the contents of your working directory
$ ls

# personally, I prefer a one column output of the contents of my working
# directory, like this:
$ ls -l

# the following command shows the text content of "note.txt" (which is empty
# right now)
$ cat note.txt

# the following command puts "hello world! I'm a snail" into "note.txt"
$ echo "hello world! I'm a snail" > note.txt

# cat will print something now that there is content in "note.txt"
$ cat note.txt

# the following command makes a copy of "note.txt" called "new-note.txt"
$ cp note.txt new-note.txt

# what is in "new-note.txt"?
$ cat new-note.txt

# * the following command opens "new-note.txt" in a terminal text editor
# * try changing the file, then press Ctrl-X to exit and save
$ nano new-note.txt

# if you were successful, this command should print the new content
$ cat new-note.txt

# if you were not successful, that is just fine. revisit this exercise after
# some more reading and practice!
```

Okay so im trying to do the Magikarp Ground Mission challenge
completed
![Challenge photo](/assets/img/MagikarpGroundmission.png)

## Forensics
"Digital Forensics is the field in cybersecurity that tries to gather and understand evidence after an incident, which can be crime, to determine how it happened."

Download the problem file in your webshell by right-clicking the link in the problem description and selecting Copy Address or Copy Link. Then download it by typing in __`wget `__ 

The next command is kind of confusing, because the first word references the program file and the second word references the file named file, but run this command and see what it tells you:

``` $ file file```

### Grep Tutorial
```
. (dot) - a single character.
? - the preceding character matches 0 or 1 times only.
* - the preceding character matches 0 or more times.
+ - the preceding character matches 1 or more times.
{n} - the preceding character matches exactly n times.
{n,m} - the preceding character matches at least n times and not more than m times.
[agd] - the character is one of those included within the square brackets.
[^agd] - the character is not one of those included within the square brackets.
[c-f] - the dash within the square brackets operates as a range. In this case it means either the letters c, d, e or f.
() - allows us to group several characters to behave as one.
| (pipe symbol) - the logical OR operation.
^ - matches the beginning of the line.
$ - matches the end of the line.
``` 

### Find Tutorial
1. find . -name thisfile.txt
If you need to know how to find a file in Linux called thisfile.txt, it will look for it in current and sub-directories.
2. find /home -name *.jpg
Look for all .jpg files in the /home and directories below it.
3. find . -type f -empty
Look for an empty file inside the current directory.
4. find /home -user randomperson-mtime 6 -iname ".db"
Look for all .db files (ignoring text case) that have been changed in the preceding 6 days by a user called randomperson.

-O1 – (Default) filter based on file name first
-O2 – File name first, then file-type
-O3 – Allow find to automatically re-order the search based on efficient use of resources and likelihood of success
-maxdepth X – Search this directory along with all sub-directories to a level of X
-iname – Search while ignoring text case.
-not – Only produce results that don’t match the test case
-type f – Look for files
-type d – Look for directories

`find . -type f -exec grep "forinstance" '{}' \; -print`

This goes through every object in the current directory tree (.) that’s a file (-type f) and then runs grep ” forinstance ” for every file that matches, then prints them on the screen (-print). 

### Disk analysis
First use of Sleuthkit 
 Something new in this challenge is using netcat or nc. For this challenge, nc is used to access a checker program. This program will check your answer to the challenge and give you the flag if it is correct.

"mmls - Display the partition layout of a volume system q(partition tables)"

I messed up because the disk was disk.img.gz but i needed to unzip it, special gunzip function
`alex-infosec-picoctf@webshell:/tmp$ gunzip disk.img.gz `
now i can 
1. Calculate the Offset
```bash 
OFFSET=$(( 2048 * 512 ))
echo $OFFSET 
```
I got 1048576 as the output. This is the offset for mounting the partition.
2. Create a Directory for Mounting and Mount the Partition
```bash
mkdir /tmp/mount-point
sudo mount -o loop,offset=1048576 disk.img /tmp/mount-point
```
oop actually I jumped the gun
__BRO I DIDNT LAUNCH THE CHALLENGE INSTANC SMH__

#### How do you find the partition lenth in sectors
start sector - end sector __DUH__
Units are in 512-byte sectors

| Slot | Start      | End        | Length     | Description     |
|------|------------|------------|------------|-----------------|
| 000: | Meta       | 0000000000 | 0000000000 | 0000000001      |
| 001: | Unallocated| 0000000000 | 000002047  | 000002048       |
| 002: | 000:000    | 000002048  | 000204799  | 000202752  

length of the partition is 202752
boom got the flag

### Packet Analysis
Requires the use of GUI took 'Wireshark'
__Downloaded wireshark__

#### Wireshark
1. Open Wireshark on your computer.
2. Click on File in the top menu.
3. Select Open... and navigate to the location of your packet capture file (usually has a .pcap or .pcapng extension).
4. Click Open, and the packets should load into Wireshark for analysis.

To filter out ARP messages, add !`arp `to your filter in Wireshark:
*'ARP' stands for Address Resolution Protocol and these messages are common in every network capture as it is needed to connect a hardware address to an IP address.*
*The TCP handshake, also known as the 'three-way handshake' can be identified by the flags in the packets. First 'SYN' from host A, the 'SYN, ACK' from host B, then finally, 'ACK' from host A. 'SYN' stands for synchronization, and 'ACK' stands for acknowledgement. Both parties synchronize and acknowledge.*
Were looking for the [PSH] flag set because it means there data for the application in the packet

#### Network Layers
1. __Application layer__: Responsible for handling data traffic between applications. HTTP belongs to this layer; HTTP protocol is commonly used to obtain Web Pages.
2. __Transport layer:__ Responsible for providing several connections on the same host, that means that you can have several applications on the same device and each of them can have a different connection even if it is just one device. It also defines functionalities for reliable transport. Two protocols are used on this layer. TCP (Transport Control Protocol). You use this protocol when you need to have reliable transport, this makes sure that if a piece of information was missing while being transfertransferred it is resent. But you want faster transport that does not resend parts that were missing, UDP (User Datagram Protocol) is used. 
3. __Network layer:__ It provides devices with an address in the network called the IP (Internet Protocol) address, and routes information through different routers. 
4. __Data link layer:__ It provides communication between devices that are connected directly. Examples of protocols in the data link layer are Ethernet or WiFi.
5. __Physical layer:__ This handles electrical pulses on the wire that represent bits.

## Programmin in python
For binary exploitation, there is a very useful library called pwntools:
http://docs.pwntools.com/en/stable
Keep this library in mind as an important part of python for exploitation. 

## Network
A network is made up of several computers connected. They can be connected through different protocols. A __Protocol__ is a set of rules that allow two computers in a network to send and receive information. 
*Wireshark is a "sniffer"*

I wasnt able to use Wireshark as they had described because I use a mac and they said i would have to install some chmod bs

## Infiltrating in a database
### Basic SQL injection
The objective of the basic SQL injection we are learning is to try to inject an "or" expression that is always true. In that way the server code constructs a query using the user input that deceives the program into it returning the whole table.
`"SELECT * FROM user where name='".$name.""' and password='".$password.""';"`
Doesnt really work in modern applications

### Blind SQL injection
Internally, the injection deceives the application into returning records, but the application did not show us those records. That’s why it is called Blind SQL injection. We can inject SQL, but we cannot see the result!

### Stack Overflow attack In the C program, there's a function called win() that should never be called.
The vuln() function takes user input using gets(), which is dangerous because it doesn't check the size of the input.
If you input too many characters, you can overflow the memory and accidentally (or intentionally) make the program run the win() function.
This is called a stack overflow attack because you're overflowing the memory (stack) to change the flow of the program.

Boom they just had a long section on assembly that I didnt want to do 