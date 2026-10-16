# URL
https://overthewire.org/wargames/bandit/bandit28.html

# Concepts
* Connect to a github repo and clone the repo.
  * Cloning git repo using ssh instead of http
* Find the password
  
# Method to Solve
* Brought up the man pages for git, which took me to the man pages for git clone
* Ran the clone command
  ```bash
  git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/
  ```
* Access the repo and cat the README. 
  
