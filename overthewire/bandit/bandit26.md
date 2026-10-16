# URL
https://overthewire.org/wargames/bandit/bandit27.html

# Concepts
* Connect to bandit26 and grab bandit27 creds
  
# Method to Solve
* Using the shell obtained from bandit26 we run
  ```bash
  ls
  ```
* This results in seeing that there is a bandit27-do file.
* I attempted using cat to see the contents of the file but it was an executable with some text.
* I then ran
  ```bash
  file bandit27-do
  strings bandit27-do
  ```
* After reviewing the human readable strings in the executable, I realized that the script would let you execute any command as bandit27
* I executed the following to get the password for bandit27
  ```bash
  ./bandit27-do cat /etc/bandit_pass/bandit27
  ```
* Successfully got the password
