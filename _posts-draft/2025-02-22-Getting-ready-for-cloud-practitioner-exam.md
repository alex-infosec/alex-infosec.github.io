
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

# AHHHHH
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

![CLI Cheat Sheet](/assets/img/CLI Cheat Sheet.png)

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